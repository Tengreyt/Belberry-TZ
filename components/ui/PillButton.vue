<template>
  <button
    class="w-full flex items-center rounded-full bg-white h-[56px] px-2 pr-6 shadow-none"
    @click="$emit('click')"
  >
    <!-- Круглая иконка слева -->
    <span
      class="flex items-center justify-center rounded-full flex-shrink-0 p-[6px] my-[2px]"
      :class="iconBgClass"
      :style="iconBgStyle"
      style="width:48px;height:48px;"
    >
      <slot name="icon">
        <IconNextMobile />
      </slot>
    </span>
    <span class="text-[#313131] text-[20px] font-bold w-full text-center select-none">
      <slot>{{ text }}</slot>
    </span>
  </button>
</template>

<script setup>
import IconNextMobile from '../icons/IconNextMobile.vue'

const props = defineProps({
  text: { type: String, default: '' },
  iconBg: { type: String, default: '#ECF96E' },
})
const iconBgClass = '' 
const iconBgStyle = `background-color: ${props.iconBg}`
</script> 