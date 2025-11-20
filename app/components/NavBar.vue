<script setup lang="ts">
import NavMenuMobile from "./NavMenuMobile.vue";

interface NavItem {
  title: string;
  link: string;
  dropdown: boolean;
  menu?: any;
}

const navItemProps = defineProps<{
  items: NavItem[];
}>();
</script>

<template>
  <UHeader
    class="dark:border border border-stroke-2 dark:border-stroke-6 backdrop-blur-lg"
    mode="slideover"
  >
    <template #title>
      <span class="sr-only">Home</span>
      <div>
        <h3>Ellen<b class="text-primary-300">Works</b></h3>
      </div>
    </template>

    <!-- <ULink
      v-for="item in navItemProps"
      exact-hash
      raw
      :to="item.link"
      class="text-lg mx-8 hover:text-primary transition-all duration-200"
      active-class="text-primary"
      inactive-class="text-2xl text-muted"
      :active="activeSection === item.to.slice(1)"
    >
      {{ item.label }}
    </ULink> -->
    <ul class="flex items-center">
      <li
        class="relative cursor-pointer py-2.5"
        v-for="item in navItemProps.items"
      >
        <UPopover v-if="item.dropdown" mode="hover">
          <ULink
            :to="item.link"
            active-class="text-primary"
            inactive-class="text-muted"
            class="group flex items-center gap-1 px-4 py-2 border border-transparent hover:border-stroke-2 dark:hover:border-stroke-7 rounded-sm text-tagline-1 font-normal text-secondary/60 hover:text-secondary transition-all duration-200 dark:text-accent/60 dark:hover:text-accent"
          >
            <span>{{ item.title }}</span>
            <UIcon
              name="i-lucide-chevron-down"
              class="size-5 ease-in-out transition-transform duration-200 group-hover:rotate-180"
            />
          </ULink>
          <template #content>
            <div class="w-40 p-3 py-1.5 flex flex-col" v-for="m in item.menu">
              <ULink class="hover:bg-zinc-700 p-2 rounded-sm" :to="m.link">
                {{ m.title }}
              </ULink>
            </div>
          </template>
        </UPopover>

        <ULink
          v-else
          :to="item.link"
          active-class="text-primary"
          inactive-class="text-muted"
          class="flex items-center gap-1 px-4 py-2 border border-transparent hover:border-stroke-2 dark:hover:border-stroke-7 rounded-sm text-tagline-1 font-normal text-secondary/60 hover:text-secondary transition-all duration-200 dark:text-accent/60 dark:hover:text-accent"
        >
          <span>{{ item.title }}</span>
        </ULink>
      </li>
    </ul>
    <template #right>
      <ULink
        class="btn btn-md btn-primary hover:btn-secondary hidden rounded-sm lg:flex"
      >
        <span class="text-accent">Contact</span>
      </ULink>
    </template>
    <template #body>
      <UAccordion :items="navItemProps.items">
        <template #trailing="{ item }">
      <!-- Only show icon if item is enabled -->
      <UIcon 
        v-if="item.dropdown" 
        name="i-lucide-chevron-down"
        class="shrink-0 size-5 ms-auto group-data-[state=open]:rotate-180 transition-transform duration-200"
      />
    </template>
        <template #default="{ item, open }">
          <ULink :to="item.link" class="block p-2 hover:bg-muted">
            {{ item.title }}
          </ULink>
        </template>
        <template #body="{ item }">
          <div class="p-5">
            <div class="py-2.5" v-for="m in item.menu">
              <ULink class="text-accent" :to="m.link">
              {{ m.title }}
              </ULink>
            </div>
          </div>
        </template>
      </UAccordion>
    </template>
  </UHeader>
  <!-- <header>
    <div
      class="mx-auto w-full fixed left-1/2 -translate-x-1/2 z-50 px-2.5 xl:py-0 py-2.5 dark:border bg-accent/60 border border-stroke-2 dark:border-stroke-6 dark:bg-background-9 backdrop-blur-lg"
    >
      <div
        class="max-w-[1290px] mx-auto lp:px-0 px-5 flex items-center justify-between"
      >
        <div>
          <a href="">
            <span class="sr-only">Home</span>
            <div>
              <h3>Ellen<b class="text-primary-300">Works</b></h3>
            </div>
            <figure class="lg:hidden block"></figure>
          </a>
        </div>
        <nav class="hidden xl:flex items-center">
          <ul class="flex items-center">
            <li
              class="relative nav-item cursor-pointer py-2.5"
              v-for="item in navItemProps.items"
            >
              <a
                :href="item.link"
                class="flex items-center gap-1 px-4 py-2 border border-transparent hover:border-stroke-2 dark:hover:border-stroke-7 rounded-full text-tagline-1 font-normal text-secondary/60 hover:text-secondary transition-all duration-200 dark:text-accent/60 dark:hover:text-accent"
              >
                <span>{{ item.title }}</span>
                <span
                class="nav-arrow block origin-center transition-all duration-300 translate-y-px"
              >
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  fill="none"
                  viewBox="0 0 24 24"
                  stroke-width="1.5"
                  stroke="currentColor"
                  class="size-4"
                >
                  <path
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    d="m19.5 8.25-7.5 7.5-7.5-7.5"
                  />
                </svg>
              </span></a>
            </li>
          </ul>
        </nav>
        <div class="xl:flex hidden items-center justify-center">
          <a
            href=""
            class="btn btn-md btn-primary hover:btn-secondary dark:btn-accent"
          >
            <span>Haha</span>
          </a>
        </div>
        <div class="xl:hidden block">
          <button @click="open = !open"
            class="nav-hamburger flex flex-col gap-[5px] size-12 bg-background-4 dark:bg-background-6 rounded-full items-center justify-center cursor-pointer"
          >
            <span class="sr-only">Menu</span>
            <span class="block w-6 h-0.5 bg-stroke-9 dark:bg-stroke-1"></span>
            <span class="block w-6 h-0.5 bg-stroke-9 dark:bg-stroke-1"></span>
            <span class="block w-6 h-0.5 bg-stroke-9 dark:bg-stroke-1"></span>
          </button>
        </div>
      </div>
    </div>
    <NavMenuMobile :open="open"/>
  </header> -->
</template>

<style scoped></style>
