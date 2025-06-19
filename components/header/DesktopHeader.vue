<template>
  <div class="bg-white hidden lg:block">
    <div class="max-w-[1280px] mx-auto flex items-center justify-between py-[10px] px-4 lg:px-0">
      <DesktopNavigation />
      <NuxtLink to="/" class="flex items-center gap-2">
        <img src="../../assets/images/logo.png" alt="Belberry" class="h-7 w-auto" />
      </NuxtLink>
      <div class="flex items-center gap-3 xl:gap-4">
        <NuxtLink
          to="/blog"
          class="relative rounded-full bg-neutral-100 pl-[12px] pr-[9px] py-[12px] text-base font-medium text-neutral-800 hover:bg-neutral-200 transition"
        >
          Блог
          <sup
            class="absolute -top-[-2px] -right-[-0px] 
                text-[14px] font-[600] leading-[113%] tracking-[0%] 
                text-right align-bottom uppercase 
                bg-gradient-to-b from-[#0804A1] to-[#9278FA] 
                bg-clip-text text-transparent font-gilroy"
          >
            31
          </sup>
        </NuxtLink>
        <NuxtLink
          to="/contacts"
          class="rounded-full bg-neutral-100 px-[12px] py-[12px] text-base font-medium text-neutral-800 hover:bg-neutral-200 transition"
        >
          Контакты
        </NuxtLink>
        <button
          @click="scrollToFooter"
          class="rounded-full bg-neutral-800 px-[26px] py-[12px]
                  text-base font-semibold text-white
                  transition-colors bg-[#313131] cursor-pointer
                  hover:bg-[#ECF96E] hover:text-black"
        >
          Связаться с нами
        </button>
      </div>
    </div>
  </div>
</template>

<script setup>
import DesktopNavigation from '~/components/DesktopNavigation.vue'
import { inject } from 'vue'
const scrollToFooter = inject('scrollToFooter')
</script> 