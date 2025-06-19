<template>
  <label class="flex items-start gap-2 cursor-pointer select-none">
    <div
      class="relative w-[18px] min-w-[18px] h-[18px] flex-shrink-0
             mt-0.5 md:mt-0"         
    >
      <input
        type="checkbox"
        :checked="modelValue"
        @change="$emit('update:modelValue', $event.target.checked)"
        class="peer absolute w-full h-full opacity-0 cursor-pointer z-10"
      />
      <div
        class="w-full h-full border border-[#8B8B8B] rounded-[4px] bg-transparent
               flex items-center justify-center z-0"
      >
        <div v-if="modelValue" class="absolute -right-[3px] top-[1px] z-20">
          <IconFooter />
        </div>
      </div>
    </div>
    <slot />
  </label>
</template>

<script setup lang="ts">
import IconFooter from '~/components/icons/IconFooter.vue'

defineProps<{ modelValue: boolean }>()
defineEmits(['update:modelValue'])
</script>
