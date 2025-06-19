<template>
  <div class="bg-white flex items-center justify-between px-4 py-2 lg:hidden">
    <!-- Бургер -->
    <button @click="$emit('toggle-menu')" class="flex items-center justify-center">
      <IconBurger class="w-8 h-8" />
    </button>
    <!-- Логотип -->
    <NuxtLink to="/" class="flex-1 flex justify-center">
      <img :src="logoMobel" alt="Belberry Mobile" class="w-[78px] h-[45px]" />
    </NuxtLink>
    <!-- Кнопка -->
    <button
      @click="scrollToFooter"
      class="ml-auto flex items-center justify-center w-[150px] h-[45px] rounded-[30px] px-[19px] pt-[13px] pb-[12px] bg-[#313131] gap-[10px]"
    >
      <span class="text-white font-semibold text-[14px] leading-[100%] tracking-[0] w-full text-center font-gilroy">Напишите нам</span>
    </button>
  </div>
</template>

<script setup>
import IconBurger from '~/components/icons/IconBurger.vue'
import logoMobel from '~/assets/images/logo-mobel.png'
import { inject } from 'vue'
const scrollToFooter = inject('scrollToFooter')
</script> 