<template>
  <ul class="hidden lg:flex gap-3 xl:gap-4">
    <li
      v-for="item in leftNav"
      :key="item.title"
      class="relative group"
      @mouseenter="activeDropdown = item.isDropdown ? item.title : null"
      @mouseleave="activeDropdown = null"
    >
      <NuxtLink
        v-if="!item.isDropdown"
        :to="item.to"
        class="flex items-center gap-1 rounded-full bg-neutral-100 px-[12px] h-[47px] text-base font-medium text-neutral-800 hover:bg-neutral-200 transition"
      >
        <span>{{ item.title }}</span>
        <sup
          class="absolute -top-0 -right-[-5px]
                  text-[14px] font-[600] leading-[113%] tracking-[0%] 
                  text-right align-bottom uppercase 
                  bg-gradient-to-b from-[#0804A1] to-[#9278FA] 
                  bg-clip-text text-transparent font-gilroy"
        >
          {{ item.count }}
        </sup>
      </NuxtLink>

      <div
        v-else
        class="flex items-center gap-1 rounded-full bg-neutral-100 px-[12px] h-[47px] text-base font-medium text-neutral-800 hover:bg-neutral-200 transition cursor-pointer"
      >
        <span>{{ item.title }}</span>
        <IconChevronSmall class="transform transition-transform group-hover:rotate-180" />
        <sup
          class="absolute -top-0 -right-[-6px] 
                    text-[14px] font-[600] leading-[113%] tracking-[0%] 
                    text-right align-bottom uppercase 
                    bg-gradient-to-b from-[#0804A1] to-[#9278FA] 
                    bg-clip-text text-transparent font-gilroy"
        >
          {{ item.count }}
        </sup>
      </div>

      <!-- ВЫПАДАЮЩЕЕ МЕНЮ (ПОЯВЛЯЕТСЯ ПРИ НАВЕДЕНИИ) -->
      <transition name="fade">
        <div
          v-if="item.isDropdown && activeDropdown === item.title"
          class="absolute left-0 top-full mt-2 w-max min-w-[280px] z-10"
        >
          <HeaderDropdown :items="item.children" :is-nested="false" />
        </div>
      </transition>
    </li>
  </ul>
</template>

<script setup>
import { ref } from 'vue'
import IconChevronSmall from '~/components/icons/IconChevronSmall.vue'
import HeaderDropdown from '~/components/HeaderDropdown.vue'

const activeDropdown = ref(null)

const leftNav = [
  { 
    title: 'Проекты', 
    to: '/projects', 
    count: '18',
  },
  {
    title: 'Услуги',
    to: '/services',
    isDropdown: true,
    count: '36',
    children: [
      { title: 'Разработка сайта на WordPress', to: '/services/clinic-website/wordpress', isDropdown: false },
      { title: 'Разработка сайта на 1С-Битрикс', to: '/services/clinic-website/bitrix', isDropdown: false },
      { title: 'Разработка сайта для стоматологии', to: '/services/clinic-website/stom', isDropdown: false },
      { title: 'Разработка Landing Page', to: '/services/clinic-website/landing', isDropdown: false },
      { title: 'Разработка личного сайта врача', to: '/services/clinic-website/doctor', isDropdown: false },
      { title: 'Разработка сайта за 3 дня', to: '/services/clinic-website/3days', isDropdown: false },
      { title: 'Разработка сайта на шаблоне', to: '/services/clinic-website/template', isDropdown: false },
      { title: 'Разработка личного кабинета клиники', to: '/services/clinic-website/cabinet', isDropdown: false },
      { title: 'Техническая поддержка для клиники', to: '/services/tech-support', isDropdown: false }
    ]
  },
  {
    title: 'Мы',
    to: '/about',
    isDropdown: true,
    children: [
      { title: 'Наша команда', to: '/about/team', isDropdown: false },
      { title: 'Наши ценности', to: '/about/values', isDropdown: false }
    ]
  }
]
</script>

<style scoped>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style> 