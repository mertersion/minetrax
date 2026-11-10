<script setup>
import { computed } from "vue";

const props = defineProps({
    active: Boolean,
    href: String,
    as: String,
    openInNewTab: {
        type: Boolean,
        default: false,
    },
});

const classes = computed(() => {
    return props.active
        ? "block ps-3 pe-4 py-2 border-s-4 border-primary text-base font-medium text-primary bg-primary/10 focus:outline-hidden focus:text-primary-foreground focus:bg-primary/20 focus:border-primary transition duration-150 ease-in-out"
        : "block ps-3 pe-4 py-2 border-s-4 border-transparent text-base font-medium text-foreground hover:text-foreground hover:bg-secondary hover:border-foreground focus:outline-hidden focus:text-foreground focus:bg-secondary focus:border-foreground transition duration-150 ease-in-out";
});
</script>

<template>
  <div>
    <button
      v-if="as == 'button'"
      :class="classes"
      class="w-full text-start"
    >
      <slot />
    </button>

    <InertiaLink
      v-else-if="as != 'button' && !openInNewTab"
      :href="href"
      :class="classes"
    >
      <slot />
    </InertiaLink>

    <a
      v-else
      target="_blank"
      :href="href"
      :class="classes"
    >
      <slot />
    </a>
  </div>
</template>
