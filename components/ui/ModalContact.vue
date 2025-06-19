<template>
  <teleport to="body">
    <div v-if="modelValue" class="fixed inset-0 z-50 flex items-center justify-center">
      <!-- Затемнение фона -->
      <div class="fixed inset-0 bg-[#02004B66]/60 backdrop-blur-sm transition-opacity" @click="$emit('update:modelValue', false)"></div>
      <!-- Модальное окно -->
      <div class="relative bg-white rounded-[24px] max-w-[800px] w-full px-12 py-12 z-10 flex flex-col items-center shadow-xl animate-fade-in">
        <!-- Кнопка закрытия -->
        <IconClose class="absolute cursor-pointer top-7 right-7 text-neutral-400 hover:text-black text-3xl" @click="$emit('update:modelValue', false)" />
        <h2 class="text-[40px] font-bold text-center mb-4 leading-[1.1]">Осталось совсем немного!</h2>
        <p class="text-center text-neutral-700 mb-8 text-lg leading-[1.4]">
          Мы рассчитали стоимость вашего сайта, она составила 320 000<br>рублей. Оставьте контакты, и наш менеджер свяжется с вами<br>в ближайшее время.
        </p>
        <form class="w-full flex flex-col gap-6">
          <div class="flex gap-4 w-full">
            <BaseInput
              v-model="name"
              label="Имя"
              class="flex-1"
            />
            <BaseInput
              v-model="phone"
              label="Телефон"
              type="tel"
              class="flex-1"
            />
          </div>
          <button type="submit" class="w-full mt-2 mb-2 cursor-pointer py-4 h-[64px] rounded-[32px] text-white font-semibold text-xl bg-gradient-to-r from-[#9278FA] to-[#5B4DF7] hover:from-[#5B4DF7] hover:to-[#9278FA] transition">Оставить заявку</button>
          <div class="flex items-start mt-2">
            <PrivacyCheckbox v-model="agree" />
            <label class="checkbox-label text-xs select-none ml-[8px] items-center">
              Нажимая кнопку, я соглашаюсь с <a href="#" class="checkbox-link">политикой конфиденциальности</a> и даю разрешение<br>на обработку моих персональных данных.
            </label>
          </div>
        </form>
      </div>
    </div>
  </teleport>
</template>

<script setup>
import { ref, watch } from 'vue';
import PrivacyCheckbox from './PrivacyCheckbox.vue';
import IconClose from '../icons/IconClose.vue';
import BaseInput from './BaseInput.vue';

const props = defineProps({
  modelValue: Boolean
});
const emit = defineEmits(['update:modelValue']);

const name = ref('');
const phone = ref('');
const agree = ref(false);
</script>

<style scoped>
@keyframes fade-in {
  from { opacity: 0; transform: scale(0.97); }
  to { opacity: 1; transform: scale(1); }
}
.animate-fade-in {
  animation: fade-in 0.2s;
}
.checkbox-label {
  font-family: 'Golos Text', sans-serif;
  font-weight: 400;
  font-size: 14px;
  line-height: 140%;
  letter-spacing: 0;
  color: #8B8B8B;
}
.checkbox-link {
  font-weight: 700;
  font-size: 14px;
  line-height: 140%;
  letter-spacing: 0;
  color: #8B8B8B;
}
</style> 