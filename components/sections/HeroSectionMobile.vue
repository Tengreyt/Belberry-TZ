<template>
  <section class="flex flex-col gap-4 px-[18px] py-4 w-full max-w-[480px] mx-auto block md:hidden">
    <!-- Верхний баннер -->
    <div class="rounded-[24px] bg-gradient-to-b from-[#0804A1] to-[#9278FA]  px-[26px] py-[30px] flex flex-col gap-4">
        <span class="text-white text-lg font-normal leading-[120%] tracking-normal">
            digital creative agency
        </span>
        <h1 class="text-white text-[25px] font-normal leading-[110%] mb-[20px] mt-[20px]">СОЗДАНИЕ<br>И ПРОДВИЖЕНИЕ<br>САЙТОВ</h1>
      <div class="flex items-center gap-[2px] mt-2">
        <button class="flex-1 w-[213px] h-[48px] rounded-full bg-white text-[#0804A1] text-[18px] font-bold flex items-center justify-center">Наши проекты</button>
        <IconMobileSection />
      </div>
    </div>
    <!-- Нижний баннер -->
    <div
      class="relative rounded-[24px] px-[29px] pb-[30px] pt-[98px] h-[250px]
             bg-gradient-to-b from-[#0804A1] to-[#9278FA] p-6"
    >
      
      <div
        :style="{ backgroundImage: `url(${rightBanner})` }" 
        class="absolute inset-0  bg-cover bg-center  mix-blend-lighten rounded-[26px] " />

      <!-- Контент поверх -->
      <div class="relative z-10 flex flex-col h-full  ">
        <div class="mb-[12px]">
          <span class="text-white text-[18px] leading-[120%]">ваша цена</span>
          <div class="text-white text-[36px] font-500 leading-[120%]">
            320 000 ₽
            <!-- можно еще написать прабел так "&nbsp;". Но я не стал этого делать. не знаю почему =) -->
          </div>
        </div>

        <!-- Кнопка‑пилюля + круг со стрелкой -->
        <PillButton text="Заказать" />
      </div>

      <!-- Иконка, выходящая за пределы блока -->
      <IconMobileThreeD class="absolute right-[-25px] bottom-0 h-[300px] pointer-events-none select-none" />
    </div>
  </section>
</template>

<script setup>
import IconMobileSection from '../icons/IconMobileSection.vue';
import IconMobileThreeD from '../icons/IconMobileThreeD.vue';
import rightBanner from '~/assets/images/right-banner.png';
import PillButton from '~/components/ui/PillButton.vue'
</script>
