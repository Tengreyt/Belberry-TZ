<template>
  <footer id="footer-desktop">
    <div class="w-full h-auto bg-[#313131] rounded-[20px] bg-cover bg-no-repeat bg-center p-[60px] flex flex-col justify-between" :style="{ backgroundImage: `url(${footerIconBg})` }">
      <div>
        <h1 class="text-[44px] font-[600] leading-[120%] text-white mb-[40px]">Посчитайте стоимость вашего сайта:</h1>

        <div class="grid grid-cols-3 gap-[20px] mb-[60px]">
          <BaseSelect placeholder="Тип сайта" :options="siteTypeOptions" v-model="form.siteType" class="col-span-1" />
          <BaseSelect placeholder="Тип CMS" :options="cmsTypeOptions" v-model="form.cmsType" class="col-span-1" />
          <BaseSelect placeholder="Тематика сайта" :options="siteThemeOptions" v-model="form.siteTheme" class="col-span-1" />
          <BaseSelect placeholder="Дизайн сайта" :options="designTypeOptions" v-model="form.designType" class="col-span-1" />
          <BaseSelect placeholder="Дополнительные услуги" :options="additionalServicesOptions" v-model="form.additionalServices" class="col-span-1" />
          <BaseTextarea placeholder="Комментарии к проекту" v-model="form.comments" class="col-span-1 row-span-2" />
        </div>

        <div class="flex items-center mb-[40px]">
          <p class="text-white text-[24px] font-[400] leading-[140%] mr-4">Стоимость проекта:</p>
          <p class="text-white text-[64px] font-[600] leading-[120%]">{{ totalPrice.toLocaleString() }} ₽</p>
        </div>

        <CTAButton class="mb-[20px]" @click="modalOpen = true">Связаться с нами</CTAButton>

        <PrivacyCheckbox v-model="form.agreeToPrivacy">
          <p class="text-[15px] font-[400] leading-[140%] flex-1 text-xs text-neutral-400 select-none min-w-0">
            Нажимая кнопку, я соглашаюсь с
            <b><a href="#" class="text-neutral-400 font-[600]"> политикой конфиденциальности</a></b>
            и даю разрешение на обработку моих персональных данных. 
          </p>
        </PrivacyCheckbox>

        <ModalContact v-model="modalOpen" :total="totalPrice" />
      </div>
    </div>
  </footer>
</template>

<script setup>
import { ref, computed } from 'vue';
import footerIconBg from '~/assets/images/footer-icon-bg.png';
import BaseSelect from '~/components/ui/BaseSelect.vue';
import BaseTextarea from '~/components/ui/BaseTextarea.vue';
import CTAButton from '~/components/ui/CTAButton.vue';
import PrivacyCheckbox from '~/components/ui/PrivacyCheckbox.vue';
import ModalContact from '~/components/ui/ModalContact.vue';

const form = ref({
  siteType: null,
  cmsType: null,
  siteTheme: null,
  designType: null,
  additionalServices: null,
  comments: '',
  agreeToPrivacy: false,
});

const modalOpen = ref(false);

const siteTypeOptions = [
  { label: 'Лендинг', value: 'landing', price: 80000 },
  { label: 'Корпоративный сайт', value: 'corporate', price: 120000 },
  { label: 'Интернет-магазин', value: 'e-commerce', price: 180000 }
];

const cmsTypeOptions = [
  { label: 'WordPress', value: 'wordpress', price: 20000 },
  { label: '1С-Битрикс', value: 'bitrix', price: 30000 },
  { label: 'Самописная', value: 'custom', price: 50000 }
];

const siteThemeOptions = [
  { label: 'Медицина', value: 'medicine', price: 10000 },
  { label: 'Недвижимость', value: 'real_estate', price: 15000 },
  { label: 'Образование', value: 'education', price: 8000 },
  { label: 'Другое', value: 'other', price: 5000 }
];

const designTypeOptions = [
  { label: 'Индивидуальный', value: 'individual', price: 40000 },
  { label: 'Шаблонный', value: 'template', price: 20000 }
];

const additionalServicesOptions = [
  { label: 'SEO-оптимизация', value: 'seo', price: 15000 },
  { label: 'Контекстная реклама', value: 'contextual_ads', price: 20000 },
  { label: 'Интеграция CRM', value: 'crm_integration', price: 25000 }
];

const totalPrice = computed(() => {
  const keys = ['siteType', 'cmsType', 'siteTheme', 'designType', 'additionalServices'];
  return keys.reduce((sum, key) => {
    const val = form.value[key];
    return sum + (val?.price || 0);
  }, 0);
});
</script>

<style scoped>
</style>