<template>
    <div class="px-[18px]">
        <footer
        id="footer-mobile"
        class="w-full bg-[#313131] relative rounded-[20px] px-[16px] py-[32px] flex flex-col gap-[10px] max-w-[480px] mx-auto block bg-cover bg-no-repeat bg-center"
        :style="{ backgroundImage: `url(${footerIconBg})` }"
        >
        <h1 class="text-[24px] font-[600] leading-[120%] text-white mb-4">Наши услуги:</h1>
        <BaseSelect placeholder="Тип сайта" :options="siteTypeOptions" v-model="form.siteType" />
        <BaseSelect placeholder="Тип CMS" :options="cmsTypeOptions" v-model="form.cmsType" />
        <BaseSelect placeholder="Тематика сайта" :options="siteThemeOptions" v-model="form.siteTheme" />
        <BaseSelect placeholder="Дизайн сайта" :options="designTypeOptions" v-model="form.designType" />
        <BaseSelect placeholder="Дополнительные услуги" :options="additionalServicesOptions" v-model="form.additionalServices" />
        <BaseTextarea placeholder="Комментарии к проекту" v-model="form.comments" />
    
        <div class="flex flex-col gap-2 my-[24px]">
            <p class="text-white text-[24px] font-[400] leading-[120%]">Стоимость проекта:</p>
            <p class="text-white text-[72px] font-[600] leading-[100%] mt-[8px] break-words break-all max-w-full overflow-hidden text-start price-mobile">
                {{ totalPrice.toLocaleString() }} ₽
            </p>
        </div>
    
        <CTAButton class="w-full mb-[6px]" @click="modalMobileOpen = true">Связаться с нами</CTAButton>
    
        <PrivacyCheckbox v-model="form.agreeToPrivacy">
            <p class="text-xs text-neutral-400 select-none mt-[-2px]">
            Нажимая кнопку, я соглашаюсь с
            <a href="#" class="text-neutral-400 font-[600]">политикой конфиденциальности</a>
            и даю разрешение на обработку моих персональных данных.
            </p>
        </PrivacyCheckbox>
    
        <ModalContactMobile v-model="modalMobileOpen" />
        </footer>
    </div>
</template>

<script setup>
import { ref, computed } from 'vue';
import BaseSelect from '~/components/ui/BaseSelect.vue';
import BaseTextarea from '~/components/ui/BaseTextarea.vue';
import CTAButton from '~/components/ui/CTAButton.vue';
import PrivacyCheckbox from '~/components/ui/PrivacyCheckbox.vue';
import ModalContactMobile from './ModalContactMobile.vue';
import footerIconBg from '~/assets/images/footer-icon-bg.png';

const form = ref({
  siteType: null,
  cmsType: null,
  siteTheme: null,
  designType: null,
  additionalServices: null,
  comments: '',
  agreeToPrivacy: false
});

const modalMobileOpen = ref(false);

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
  { label: 'Другое', value: 'other', price: 5000 },
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
.price-mobile {
  word-break: break-all;
  overflow-wrap: break-word;
  max-width: 100%;
  display: block;
}
</style>

