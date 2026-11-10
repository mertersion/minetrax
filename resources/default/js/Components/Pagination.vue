<template>
  <div class="mt-6 -mb-1 flex flex-wrap">
    <template
      v-for="(link, key) in links"
      :key="key"
    >
      <div
        v-if="link.url === null"
        class="me-1 mb-1 px-4 py-3 text-sm border rounded text-foreground"
        :class="{'ms-auto': link.label ==='Next &raquo;'}"
        v-html="link.label"
      />
      <inertia-link
        v-else
        class="me-1 mb-1 px-4 py-3 text-sm border rounded hover:bg-white focus:border-primary focus:text-primary"
        :class="{'bg-white shadow': link.active,'bg-muted': !link.active,'ms-auto': link.label ==='Next &raquo;'}"
        :href="link.url"
      >
        <span v-html="link.label" />
      </inertia-link>
    </template>
  </div>
</template>

<script>
export default {
    props: {
        links: Array,
    },
};
</script>
