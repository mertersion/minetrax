<template>
  <div class="flex items-center p-3">
    <inertia-link
      :href="href"
      :class="classes"
    >
      <span class="me-2">
        <slot name="icon" />
      </span>
      <span>
        <slot />
      </span>
    </inertia-link>
  </div>
</template>

<script>
export default {
    props: ["href","active"],

    computed: {
        classes() {
            return this.active
                ?"bg-primary -ms-3 cursor-pointer flex items-center px-6 py-2 rounded-e-full text-white w-full transition duration-150 ease-in-out"
                :"cursor-pointer -ms-3 flex items-center px-6 py-2 rounded-e-full text-foreground dark:text-foreground w-full transition duration-150 ease-in-out hover:bg-primary dark:hover:bg-accent";
        }
    }
};
</script>
