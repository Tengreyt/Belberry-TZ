<template>
    <div class="relative w-full">
      <!-- поле -->
      <input
        :id="uid"
        :type="type"
        placeholder=" "
        v-model="localValue"
        :autocomplete="autocomplete"
        class="peer block w-full h-[60px] rounded-[12px]
               bg-neutral-100 px-6
               pt-[33px]                
               pb-[13px]                
               text-lg text-neutral-900
               placeholder-transparent outline-none
               border border-transparent focus:border-primary-500
               transition-colors" />
  
      <!-- лейбл -->
      <label
        :for="uid"
        class="pointer-events-none absolute left-6 text-neutral-400
               transition-[top,font-size,color] duration-150
               top-[22px]
               peer-placeholder-shown:top-[22px]
               peer-placeholder-shown:text-lg
               peer-focus:top-[10px]                    
               peer-focus:text-sm
               peer-focus:text-primary-500
               peer-not-placeholder-shown:top-[10px]    
               peer-not-placeholder-shown:text-sm">
        {{ label }}
      </label>
    </div>
</template>

<script setup>
import { computed } from 'vue'

const props = defineProps({
  modelValue:    { type: [String, Number], default: '' },
  label:         { type: String, required: true },
  type:          { type: String, default: 'text' },
  autocomplete:  { type: String, default: 'off' }
})
const emit = defineEmits(['update:modelValue'])

const localValue = computed({
  get: () => props.modelValue,
  set: value => emit('update:modelValue', value)
})

const uid = `input-${Math.random().toString(36).slice(2, 9)}`
</script>
  