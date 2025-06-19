<template>
  <section class="w-full max-w-[480px] mx-auto block md:hidden px-[20px] my-[60px]">
    <h2 class="services-title mb-[24px]">Наши услуги</h2>
    <div class="flex flex-col gap-3">
      <div
        v-for="(service, i) in services"
        :key="i"
        class="bg-white rounded-[16px] px-4 py-3 shadow-sm"
      >
        <div class="text-[18px] font-bold mb-[32px] gradient-title" v-html="service.title"></div>
        <div class="text-[#6B6B6B] text-[14px] leading-[130%]" v-html="service.description"></div>
      </div>
    </div>
  </section>
</template>

<script setup>
const services = [
  {
    title: 'Landing page',
    description: 'Лендинги с адаптивным дизайном для всех типов устройств',
    color: 'text-[#4B4BFA]'
  },
  {
    title: 'Внедрение BITRIX24',
    description: 'Оформление интерфейсов <br> под устройства',
    color: 'text-[#6B5BFF]'
  },
  {
    title: 'Интернет-магазин',
    description: 'Удобные интерфейсы с фокусом<br>на мобильную версию',
    color: 'text-[#4B4BFA]'
  },
  {
    title: 'Личный кабинет',
    description: 'Интуитивно понятные личные кабинеты',
    color: 'text-[#6B5BFF]'
  },
  {
    title: 'Техническая поддержка',
    description: 'Лендинги с адаптивным дизайном для всех типов устройств',
    color: 'text-[#4B4BFA]'
  },
  {
    title: 'Сайты на WordPress',
    description: 'Оформление интерфейсов<br>под устройства.',
    color: 'text-[#6B5BFF]'
  },
  {
    title: 'Проектирование интерфейса',
    description: 'Удобные интерфейсы с фокусом<br>на мобильную версию',
    color: 'text-[#6B5BFF]'
  }
]
</script>

<style scoped>
.services-title {
  font-family: 'Golos Text', sans-serif;
  font-weight: 600;
  font-size: 36px;
  line-height: 100%;
  letter-spacing: 0;
  vertical-align: middle;
  color: #4B4B4B;
}

.gradient-title {
  background: linear-gradient(90deg, #0804A1 0%, #9278FA 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  color: transparent;
}
</style> 