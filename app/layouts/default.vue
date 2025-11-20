<template>
  <div class="flex flex-col">
    <NavBar :items="processedNavItems" />
    <UMain class="mx-auto w-full">
      <slot />
    </UMain>
    <Footer :items="footerSocial" :company="footerCompany" :support="footerSupport" :legal="footerLegal"  />
  </div>
</template>

<script setup lang="ts">
import NavBar from "~/components/NavBar.vue";
import Footer from "~/components/Footer.vue";
import type { FooterPageLink } from "~/components/Footer.vue"
import type { FooterSocial } from "~/components/Footer.vue"

const navMenus: { title: string; link: string; }[] = [
  {
    title: 'Title 1', link: '#'
  },
  {
    title: 'Title 2', link: '#'
  },
  {
    title: 'Title 3', link: '#'
  },
  {
    title: 'Title 4', link: '#'
  },
  {
    title: 'Title 5', link: '#'
  }
]

const navItems = [
  {
    title: "Special",
    link: "#",
    dropdown: false,
  },
  {
    title: "About",
    link: "#",
    dropdown: true,
    menu: navMenus
  },
];

const processedNavItems = navItems.map(item => ({
  ...item,
  disabled: !item.dropdown,
  ui: {
    trailingIcon: !item.dropdown ? 'hidden': ''
  }
}))

const footerSocial: FooterSocial[] = [
  {
    title: 'Facebook', link: '#', icon: 'mdi-facebook'
  },
  {
    title: 'Whatsapp', link: '#', icon: 'mdi-whatsapp'
  },
  {
    title: 'Twitter', link: '#', icon: 'mdi-twitter'
  },
]

const footerCompany = [
  { title: 'Title A', link: '#' },
  { title: 'Title B', link: '#' },
  { title: 'Title C', link: '#' },
]

const footerSupport = [
  { title: 'Title A', link: '#' },
  { title: 'Title B', link: '#' },
  { title: 'Title C', link: '#' },
]

const footerLegal = [
  { title: 'Title A', link: '#' },
  { title: 'Title B', link: '#' },
  { title: 'Title C', link: '#' },
]
</script>

<style scoped></style>
