<script setup>
import AdminSideMenu from "@/Shared/AdminSideMenu.vue";
import MainNavbarCustom from "@/Shared/MainNavbarCustom.vue";
import { useStorage } from "@vueuse/core";
import BaseLayout from "./BaseLayout.vue";

let isMenuCollapsed = useStorage("is-admin-sidebar-menu-collapsed", false);
function toggleMenuCollapse() {
    isMenuCollapsed.value = !isMenuCollapsed.value;
}
</script>

<template>
  <BaseLayout>
    <!-- Admin NavBar -->
    <MainNavbarCustom />

    <AdminSideMenu
      :collapsed="isMenuCollapsed"
      @toggle-collapse="toggleMenuCollapse"
    />

    <main
      :class="[
        isMenuCollapsed ? 'ms-16' : 'ms-64'
      ]"
    >
      <slot />
    </main>
  </BaseLayout>
</template>
