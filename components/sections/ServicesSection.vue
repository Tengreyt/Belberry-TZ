<template>
    <section class="mt-[80px] mb-[80px]">
        <div class="max-w-[1280px] mx-auto px-4 lg:px-0">
            <h2 class="text-[#4B4B4B] font-sans text-[64px] font-[600] leading-[120%] tracking-[0%] mb-[40px] ">Наши услуги</h2>
            <div class="relative w-full">
                <!-- Тут у нас слайдер с использованием swiper -->
                <swiper
                    ref="mySwiper"
                    class="my-swiper"
                    :slides-per-view="'auto'"
                    :space-between="20"
                    :navigation="{
                        prevEl: '.swiper-button-prev-custom',
                        nextEl: '.swiper-button-next-custom'
                    }"
                    :modules="[Navigation]"
                    :watch-overflow="true"
                    :round-lengths="true"
                    :set-wrapper-size="true"
                    @swiper="setSwiperInstance"
                    :breakpoints="{
                        320: {
                            slidesPerView: 1,
                            spaceBetween: 20
                        },
                        640: {
                            slidesPerView: 2,
                            spaceBetween: 20
                        },
                        1024: {
                            slidesPerView: 3,
                            spaceBetween: 20
                        },
                        1280: {
                            slidesPerView: 3,
                            spaceBetween: 20
                        }
                    }"
                >
                    <swiper-slide v-for="(service, index) in services" :key="index" class="!w-[413px]">
                        <ServiceCard 
                            class="flex flex-col justify-between"
                            :title="service.title" 
                            :description="service.description" 
                        />
                    </swiper-slide>
                </swiper>
                
                <div class="flex justify-start mt-8">
                    <button class="swiper-button-prev-custom cursor-pointer w-[70px] h-[70px] bg-white border border-neutral-200 rounded-[10px] flex items-center justify-center mr-[10px]">
                        <IconRight class="transform rotate-180" />
                    </button>
                    <button class="swiper-button-next-custom cursor-pointer w-[70px] h-[70px] bg-white border border-neutral-200 rounded-[10px] flex items-center justify-center">
                        <IconRight />
                    </button>
                </div>
            </div>
        </div>
    </section>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import IconRight from '~/components/icons/IconRight.vue';
import ServiceCard from '~/components/ui/ServiceCard.vue';
import { Swiper, SwiperSlide } from 'swiper/vue';
import 'swiper/css';
import 'swiper/css/navigation';
import { Navigation } from 'swiper/modules';

const swiperInstance = ref(null);
const setSwiperInstance = (swiper) => {
  swiperInstance.value = swiper;
};

onMounted(() => {
  if (swiperInstance.value) {
    swiperInstance.value.update();
  }
});

const services = [
    {
        title: 'Landing<br>page',
        description: 'Лендинги с адаптивным дизайном для всех типов устройств'
    },
    {
        title: 'Внедрение BITRIX24',
        description: 'Оформление интерфейсов<br>под устройства'
    },
    {
        title: 'Интернет-магазин',
        description: 'Удобные интерфейсы с фокусом<br>на мобильную версию'
    },
    {
        title: 'Личный кабинет',
        description: 'Интуитивно понятные личные кабинеты'
    },
    {
        title: 'Техническая поддержка',
        description: 'Лендинги с адаптивным дизайном для всех типов устройств'
    },
    {
        title: 'Сайты на WordPress',
        description: 'Оформление интерфейсов<br>под устройства.'
    },
    {
        title: 'Проектирова<br>ние интерфейса',
        description: 'Удобные интерфейсы с фокусом<br>на мобильную версию'
    }
];
</script>

<style scoped>
.my-swiper {
    padding-bottom:2px;
    width: 100%;
}

.my-swiper .swiper-wrapper {
    display: flex;
    flex-direction: row;
}

.my-swiper .swiper-slide {
    flex-shrink: 0;
    width: 413px; 
}

.swiper-button-prev-custom.swiper-button-disabled,
.swiper-button-next-custom.swiper-button-disabled {
    opacity: 0.5;
    cursor: not-allowed;
}
</style> 