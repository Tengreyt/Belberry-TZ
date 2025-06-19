<template>
    <div class="flex items-start">
      <label class="flex items-start cursor-pointer space-x-2">
        <div class="relative flex items-center justify-center w-5 h-5 border-2 border-[#A87FF3] rounded-[4px]">
          <input
            type="checkbox"
            v-model="form.agreeToPrivacy"
            class="absolute inset-0 opacity-0 cursor-pointer peer"
          />
          <!-- Галочка, появляется при checked -->
          <svg
            v-if="form.agreeToPrivacy"
            class="w-4 h-4 text-[#A87FF3]"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
            stroke-width="3"
          >
            <path stroke-linecap="round" stroke-linejoin="round" d="M5 13l4 4L19 7" />
          </svg>
        </div>
        <span class="text-white text-[15px] font-[400] leading-[140%]">
          Нажимая кнопку, я соглашаюсь с
          <a href="#" class="text-white font-[600]"> политикой конфиденциальности </a>
          и даю разрешение на обработку моих персональных данных.
        </span>
      </label>
    </div>
</template>

<script setup>
const form = reactive({
  agreeToPrivacy: false,
});
</script>
  