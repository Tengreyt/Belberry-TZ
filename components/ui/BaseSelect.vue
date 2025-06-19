<template>
  <div class="relative w-full">
    <select
      class="appearance-none w-full bg-white rounded-[12px] md:rounded-[20px] py-[15px] px-[20px] text-[16px] md:text-[18px] leading-[140%] font-[400] focus:outline-none focus:ring-2 focus:ring-brand-blue-light pr-10 cursor-pointer border border-transparent focus:border-[#9278FA] transition"
      :value="modelValue?.value || ''"
      @change="onChange"
    >
      <option value="">{{ placeholder }}</option>
      <option v-for="option in options" :key="option.value" :value="option.value">
        {{ option.label }}
      </option>
    </select>
    <div class="pointer-events-none absolute inset-y-0 right-0 flex items-center pr-3 text-neutral-800">
      <svg class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
      </svg>
    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  modelValue: {
    type: [Object, String, Number],
    default: null
  },
  placeholder: {
    type: String,
    default: ''
  },
  options: {
    type: Array,
    default: () => []
  }
})

const emit = defineEmits(['update:modelValue'])

function onChange(e) {
  const val = e.target.value
  if (val === '') {
    emit('update:modelValue', null)
  } else {
    const selected = props.options.find(opt => opt.value == val)
    emit('update:modelValue', selected || null)
  }
}
</script>
