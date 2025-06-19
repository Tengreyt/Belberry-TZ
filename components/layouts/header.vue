<template>
  <header class="w-full">
    <DesktopHeader />
    <MobileHeader @toggle-menu="mobileOpen = !mobileOpen" />
    <MobileMenu :is-open="mobileOpen" @close="mobileOpen = false" />
  </header>
</template>

<script setup>
import { ref, provide } from 'vue'
import MobileMenu from '~/components/MobileMenu.vue'
import DesktopHeader from '~/components/header/DesktopHeader.vue'
import MobileHeader from '~/components/header/MobileHeader.vue'

const mobileOpen = ref(false)

const scrollToFooter = () => {
  const isMobile = window.innerWidth < 768
  const footer = document.getElementById(isMobile ? 'footer-mobile' : 'footer-desktop')
  if (footer) {
    footer.scrollIntoView({ behavior: 'smooth' })
  }
}
provide('scrollToFooter', scrollToFooter)
</script>

<style>
/* простая fade‑анимация для мобильного меню */
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.2s;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>
