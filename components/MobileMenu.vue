<template>
  <transition name="fade">
    <nav
      v-if="isOpen"
      class="lg:hidden bg-white shadow-inner"
    >
      <ul class="flex flex-col gap-1 p-4">
        <li
          v-for="item in fullNav"
          :key="item.title"
        >
          <NuxtLink
            :to="item.to"
            class="flex items-center justify-between rounded-md px-4 py-2 text-base font-medium text-neutral-800 hover:bg-neutral-100 transition"
            @click="closeMenu"
          >
            <span>{{ item.title }}</span>
            <span
              v-if="item.count"
              class="text-[14px] font-[600] leading-[113%] tracking-[0%] 
                     text-right align-bottom uppercase 
                     bg-gradient-to-b from-[#0804A1] to-[#9278FA] 
                     bg-clip-text text-transparent font-gilroy"
            >
              {{ item.count }}
            </span>
          </NuxtLink>
        </li>

        <Button
          to="/contact-us"
          text="Связаться с нами"
          @click="closeMenu"
        />
      </ul>
    </nav>
  </transition>
</template>

<script setup>
import Button from '~/components/ui/Button.vue'

const props = defineProps({
  isOpen: {
    type: Boolean,
    required: true
  }
})

const emit = defineEmits(['close'])

const closeMenu = () => {
  emit('close')
}

const fullNav = [
  { title: 'Проекты', to: '/projects', count: '18' },
  { title: 'Услуги', to: '/services', count: '36' },
  { title: 'Мы', to: '/about' },
  { title: 'Кейсы', to: '/cases' },
  { title: 'Отзывы', to: '/reviews' },
  { title: 'Блог', to: '/blog' },
  { title: 'Компания', to: '/company' },
  { title: 'Контакты', to: '/contacts' }
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