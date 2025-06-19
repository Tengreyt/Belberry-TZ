<template>
  <NuxtLink
    :to="to"
    class="mt-3 rounded-md bg-neutral-800 px-4 py-2 text-center text-sm font-semibold text-white transition hover:bg-brand-yellow hover:text-neutral-800"
    @click="$emit('click')"
  >
    <slot>{{ text }}</slot>
  </NuxtLink>
</template>

<script setup>
defineProps({
  to: {
    type: String,
    default: '/'
  },
  text: {
    type: String,
    default: ''
  }
})

defineEmits(['click'])
</script> 