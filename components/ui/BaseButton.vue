<!-- components/AnimatedButton.vue -->
<template>
  <button
    class="group relative flex h-10 w-[141px] items-center overflow-hidden rounded-full border border-white bg-white text-[#313131] font-medium transition-colors duration-300"
  >
    <!-- Жёлтая плашка‑фон -->
    <div
      class="absolute inset-1 z-0 rounded-full bg-[#ECF96E] transition-[width] duration-300 ease-in-out
             w-8 group-hover:w-[calc(100%-8px)]"
    />

    <!-- Иконка -->
    <div
      class="pointer-events-none absolute left-3 top-1/2 z-10 -translate-y-1/2
             transition-transform duration-300 ease-in-out
             group-hover:translate-x-[88px]"        
    >
      <IconButtonRight class="text-[#313131]" />
    </div>

    <!-- Текст -->
    <span
      class="ml-12 whitespace-nowrap z-10 transition-[margin] duration-300 ease-in-out
             group-hover:ml-4"
    >
      <slot />
    </span>
  </button>
</template>

<script setup lang="ts">
import IconButtonRight from '~/components/icons/IconButtonRight.vue'
</script>
