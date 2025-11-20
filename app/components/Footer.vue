<template>
  <UFooter class="bg-secondary dark:bg-background-8 relative overflow-hidden">
    <div class="pointer-events-none select-none absolute size-[200px] md:size-[770px] lg:size-[630px] xl:size-[700px] bottom-[-33%] md:bottom-[-60%] xl:bottom-[-77%] left-[-83%] md:left-[-52%] lg:left-[-38%] xl:left-[-30%] 2xl:left-[-22%] min-[2559px]:left-[-16%]! opacity-60">
      <svg viewBox="-120 -120 240 240" xmlns="http://www.w3.org/2000/svg">
                              <path d="M 81.60918382659169,0 C 86.84610886861924,23.024450067000025 94.60940091515705,35.4371450920347 82.12733733467206,52.780034863733505 C 69.64527375418707,70.12292463543231 54.389237107002,67.42886371536234 31.680929504651726,69.37155908679524 C 8.972621902301452,71.31425445822815 11.42198019357715,63.80533751105617 -8.705893074729028,60.550816349465144 C -28.833766343035208,57.296295187874115 -28.100618953828548,64.76524737890614 -48.830563568572984,56.35347444043112 C -69.56050818331742,47.9417015019561 -88.61444074717099,45.460757123162395 -91.62567153370678,26.903724595565063 C -94.63690232024257,8.346692067967727 -69.86547001423202,4.911697135239326 -60.87548671471615,-17.87465566995822 C -51.88550341520028,-40.66100847515577 -68.0201764132294,-48.78777724251205 -55.6657383356433,-64.24168662522511 C -43.3113002580572,-79.69559600793818 -31.842286540767653,-81.58751301966204 -11.457734404371758,-79.69029320081046 C 8.926817732024139,-77.79307338195888 7.713127317206876,-66.74593929895477 25.87247020994029,-56.65280734981881 C 44.0318131026737,-46.55967540068284 47.24545876239904,-53.480967241721295 61.17963716656189,-39.317765404266595 C 75.11381557072474,-25.154563566811895 76.37225878456414,-23.024450067000025 81.60918382659169,0 Z" fill="#F26B38" />
                              </svg>
    </div>
    <template #left>
      <div>
        <div
          class="grid grid-cols-12 xl:pt-[90px] gap-x-0 gap-y-16 pt-16 pb-12 justify-between"
        >
          <div class="col-span-12 xl:col-span-4">
            <div class="max-w-[306px]">
              <h3 class="text-accent">
                Ellen<b class="text-primary-300">Works</b>
              </h3>
              <p class="text-accent/60 font-normal text-tagline-1 mt-4 mb-7">
                Turpis tortor nunc sed amet et faucibus vitae morbi congue sed
                id mauris.
              </p>
              <div class="flex items-center gap-3">
                <ULink
                  class="text-accent transition-colors duration-300 hover:text-muted"
                  v-for="f in footerItemProps.items"
                  :to="f.link"
                >
                  <span class="sr-only">
                    {{ f.title }}
                  </span>
                  <div class="group px-4 py-1 rounded-full bg-accent text-black">
                    <UIcon :name="f.icon" class="size-6 group-hover:-translate-y-1 transition-all duration-200" :alt="f.title" />
                  </div>
                </ULink>
              </div>
            </div>
          </div>
        </div>
      </div>
    </template>
    <template #right>
<div class="w-full grid grid-cols-12 gap-x-12 gap-y-8">
      <div v-if="footerItemProps.company" class="col-span-12 md:col-span-4">
        <div class="space-y-8">
          <p
            class="sm:text-heading-6 text-tagline-1 font-normal text-primary-50"
          >
            Company
          </p>
          <ul class="sm:space-y-5 space-y-3">
            <li v-for="f in footerItemProps.company">
              <ULink :to="f.link" class="footer-link">
                {{ f.title }}
              </ULink>
            </li>
          </ul>
        </div>
      </div>

      <div v-if="footerItemProps.support" class="col-span-12 md:col-span-4">
        <div class="space-y-8">
          <p
            class="sm:text-heading-6 text-tagline-1 font-normal text-primary-50"
          >
            Support
          </p>
          <ul class="sm:space-y-5 space-y-3">
            <li v-for="f in footerItemProps.support">
              <ULink :to="f.link" class="footer-link">
                {{ f.title }}
              </ULink>
            </li>
          </ul>
        </div>
      </div>

      <div v-if="footerItemProps.legal" class="col-span-12 md:col-span-4">
        <div class="space-y-8">
          <p
            class="sm:text-heading-6 text-tagline-1 font-normal text-primary-50"
          >
            Legal Policies
          </p>
          <ul class="sm:space-y-5 space-y-3">
            <li v-for="f in footerItemProps.legal">
              <ULink :to="f.link" class="footer-link">
                {{ f.title }}
              </ULink>
            </li>
          </ul>
        </div>
      </div>
    </div>
    </template>
    <template #bottom>
      <p class="text-muted text-center">Copyright ©EllenWorks {{ new Date().getFullYear() }} - Frontend Work Studio</p>
    </template>
  </UFooter>
</template>

<script setup lang="ts">
export interface FooterSocial {
  title: string;
  link: string;
  icon: string;
}

export interface FooterPageLink {
  title: string;
  link: string;
}

const footerItemProps = defineProps<{
  items: FooterSocial[];
  company: FooterPageLink[] | null;
  support: FooterPageLink[] | null;
  legal: FooterPageLink[] | null;
}>();
</script>

<style scoped></style>
