<template>
  <UApp>
    <NuxtLayout>
      <NuxtPage />
    </NuxtLayout>
  </UApp>
</template>

<script setup lang="ts">
useHead({
  title: 'Some title',
  meta: [
    { name: 'description', content: 'Some description' },
      { name: 'keywords', content: 'Some keywords' },
      { name: 'author', content: 'Some author' },
      { name: 'og:title', content: 'Some title' },
      { name: 'og:description', content: 'Some description' },
      { name: 'og:image', content: 'Some image' },
      { name: 'og:url', content: 'Some url' },
      { name: 'twitter:title', content: 'Some title' },
      { name: 'twitter:description', content: 'Some description' },
      { name: 'twitter:image', content: 'Some image url' },
      { name: 'twitter:card', content: 'summary_large_image' },
  ]
})

import '../animation/accordion';
// import '../animation/glossary';
// import '../animation/gradient-path';
import '../animation/header';
// import '../animation/marquee';
import '../animation/modal';
import '../animation/sidebar';
// import '../animation/slider';
// import '../animation/svg-draw';
// import '../animation/swiper';
// import '../animation/tab';
// import '../animation/tab-filter';
// import '../common/common';
// import '../common/mobile-menu';
// import '../common/navigation-menu';
// import '../common/parallax-effect';
// import '../common/price-switcher';
// import '../common/progress';
// import '../common/reveal-elements';
// import '../common/smooth-scrolling';
// import '../utils/cookie';
// import '../utils/counter';
// import '../utils/force-theme-switcher';
// import '../utils/img-before-after-slider';
// import '../utils/leaflet';
// import '../utils/theme-switcher';
</script>