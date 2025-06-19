<template>
    <section class="flex gap-[20px]">
        <!-- Левый баннер -->
        <div class="w-[847px] h-[600px] flex flex-col justify-between rounded-[20px] p-[60px] bg-gradient-to-b from-[#0804A1] to-[#9278FA]">
            <div>
                <h3 class="text-white text-[20px] font-[400] mb-[16px]">digital creative agency</h3>
                <h1 class="text-white text-[68px] font-[500] leading-tight mb-[60px]">Создание и продвижение <br>сайтов</h1>
            </div>
            <div>
                <div :style="{ backgroundImage: `url(${bgImg})` }" class="w-full group relative items-end flex gap-3 bg-cover bg-no-repeat bg-center rounded-4 p-2.5 group">
                    <!-- Обертка для изображений с hover-эффектом -->
                    <div class="flex gap-3">
                    <div class="cursor-pointer transition-all duration-300 hover:brightness-100 group-hover:brightness-75">
                        <img :src="Img" alt="Проект 1" class="transition-all duration-300">
                    </div>
                    <div class="cursor-pointer transition-all duration-300 hover:brightness-100 group-hover:brightness-75">
                        <img :src="Img1" alt="Проект 2" class="transition-all duration-300">
                    </div>
                    <div class="cursor-pointer transition-all duration-300 hover:brightness-100 group-hover:brightness-75">
                        <img :src="Img2" alt="Проект 3" class="transition-all duration-300">
                    </div>
                    <div class="cursor-pointer transition-all duration-300 hover:brightness-100 group-hover:brightness-75">
                        <img :src="Img3" alt="Проект 4" class="transition-all duration-300">
                    </div>
                    <div class="cursor-pointer transition-all duration-300 hover:brightness-100 group-hover:brightness-75">
                        <img :src="Img4" alt="Проект 5" class="transition-all duration-300">
                    </div>
                    </div>

                    <p class="font-['Golos_Text'] font-medium text-base leading-[1.2] tracking-normal mr-auto">
                    Наши проекты
                    </p>

                    <!-- Иконка с анимацией вниз при наведении -->
                    <IconArrowNext class="absolute right-0.5 -top-1 transition-transform duration-300 rotate-0 group-hover:rotate-45" />
                </div>
            </div>
        </div>
        
        <!-- Правый баннер -->
        <div :style="{ backgroundImage: `url(${rightBanner})` }" class="w-[413px] relative bg-cover bg-no-repeat bg-center rounded-[16px] flex flex-col justify-between ">
            <div class=" flex justify-end mt-[53px] mr-[20px]">
                <p class="text-[#ECF96E] w-[190px] font-normal text-[16px] leading-[100%] tracking-normal text-right">
                техподдержка сайта <br>на 30 дней – в подарок
                </p>
            </div>

            <div class="flex-grow flex items-end justify-center px-8">
                <p class="text-white font-medium text-[70px] leading-[100%] tracking-normal z-2 mb-[34px]">
                    320 000 ₽
                </p>
            </div>

        
            <div class="relative flex justify-between">
                <div class="flex items-start">
                    <p class="text-[#313131] w-[244px] mb-[10px] font-medium text-[15px] leading-[120%] ">
                        Топ-10 самых креативных<br>разработчиков сайтов в России
                    </p>
                </div>
                <div class="absolute z-2 right-1 bottom-2">
                    <BaseButton class="cursor-pointer">Заказать</BaseButton>
                </div>
            </div>

            <IconTrheeD class="absolute right-0 botton-0 z-1"/>

        </div>
    </section>
</template>

<script setup>
import IconArrowNext from '~/components/icons/IconArrowNext.vue';
import IconTrheeD from '~/components/icons/IconTrheeD.vue';
import BaseButton from '~/components/ui/BaseButton.vue';

import bgImg from '~/assets/images/bg-img.png';
import Img from '~/assets/images/Img.png';
import Img1 from '~/assets/images/Img (1).png';
import Img2 from '~/assets/images/Img (2).png';
import Img3 from '~/assets/images/Img (3).png';
import Img4 from '~/assets/images/Img (4).png';
import rightBanner from '~/assets/images/right-banner.png';

</script>
