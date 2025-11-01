<template>
    <div class="flex flex-col">
        <NavBar />
        <UMain class="mx-auto w-full max-w-(--ui-container)">
            <slot />
        </UMain>
        <Footer />
    </div>
</template>

<script setup lang="ts">
import NavBar from '~/components/NavBar.vue';
import Footer from '~/components/Footer.vue';
</script>

<style scoped>

</style>