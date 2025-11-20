<script setup lang="ts">
interface MobileNavItem {
  title: string;
  link: string;
  submenu?: any;
}

const navProps = defineProps<{
    open: boolean;
}>()
</script>

<template>
    <!-- =========================
Mobile Menu
===========================-->
<USlideover v-model:open="navProps.open">
  <div>
    
  </div>
</USlideover>
</template>

<style scoped>

</style>