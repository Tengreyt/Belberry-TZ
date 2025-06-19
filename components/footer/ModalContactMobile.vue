<template>
    <teleport to="body">
      <transition name="fade">
        <div v-if="modelValue" class="fixed inset-0 z-50 flex items-center p-[] justify-center md:hidden">
          <!-- Затемнение фона -->
          <div
            class="fixed inset-0 bg-[#02004B66] backdrop-blur-[12px]"
            @click="$emit('update:modelValue', false)"
          ></div>

  
          <!-- Модалка -->
          <div class="relative bg-white rounded-[20px] w-[94vw] max-w-[370px] px-5 py-8 z-10 flex flex-col items-center shadow-[0_8px_40px_rgba(0,0,0,0.15)] animate-fade-in">
            <IconCloseWhite
              class="absolute top-[-35px] right-[7px] cursor-pointer text-white text-2xl"
              @click="$emit('update:modelValue', false)"
            />
  
            <h2 class="text-[24px] font-bold text-center leading-tight mb-3">
              Осталось совсем немного!
            </h2>
  
            <p class="text-center text-neutral-700 text-sm leading-[1.4] mb-[32px]">
              Мы рассчитали стоимость вашего сайта, она составила 320 000 рублей. Оставьте контакты, и наш менеджер свяжется с вами в ближайшее время.
            </p>
  
            <form class="w-full flex flex-col gap-4">
              <BaseInput
                v-model="name"
                label="Имя"
                type="text"
                autocomplete="name"
              />
              <BaseInput
                v-model="phone"
                label="Телефон"
                type="tel"
                autocomplete="tel"
              />
  
              <button
                type="submit"
                class="w-full h-[48px] mt-1 mb-1 cursor-pointer rounded-[24px] text-white text-[16px] font-semibold bg-gradient-to-r from-[#9278FA] to-[#5B4DF7] hover:from-[#5B4DF7] hover:to-[#9278FA] transition"
              >
                Оставить заявку
              </button>
  
              <div class="flex items-start mt-1">
                <PrivacyCheckbox v-model="agree" class="top-1" />
                <label class="text-[13px] leading-[140%] text-[#8B8B8B] select-none ml-2 ">
                  Нажимая кнопку, я соглашаюсь<br>с
                  <a href="#" class="font-bold text-[#8B8B8B]">политикой конфиденциальности</a><br>
                  и даю разрешение на обработку моих<br>персональных данных.
                </label>
              </div>
            </form>
          </div>
        </div>
      </transition>
    </teleport>
</template>

<script setup>
import { ref } from 'vue';
import PrivacyCheckbox from '~/components/ui/PrivacyCheckbox.vue';
import BaseInput from '../ui/BaseInput.vue';
import IconCloseWhite from '../icons/IconCloseWhite.vue';

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
  from {
    opacity: 0;
    transform: scale(0.97);
  }
  to {
    opacity: 1;
    transform: scale(1);
  }
}
.animate-fade-in {
  animation: fade-in 0.2s ease;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.2s ease;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>
  