<template>
  <textarea
    class="w-full bg-white rounded-[10px] py-[15px] px-[20px] text-neutral-800 text-[18px] leading-[140%] font-[400] focus:outline-none focus:ring-2 focus:ring-brand-blue-light resize-none"
    :value="modelValue"
    @input="$emit('update:modelValue', $event.target.value)"
    :placeholder="placeholder"
    rows="6"
  ></textarea>
</template>

<script setup>
defineProps({
  modelValue: {
    type: String,
    default: ''
  },
  placeholder: {
    type: String,
    default: ''
  }
})

defineEmits(['update:modelValue'])
</script>
