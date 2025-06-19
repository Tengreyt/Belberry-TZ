<template>
    <main class="mt-[40px]">
        <div class="hidden md:block">
            <HeroSection />
        </div>
        <div class="block md:hidden">
            <HeroSectionMobile />
        </div>
        <div class="hidden md:block">
            <ServicesSection />
        </div>
        <div class="block md:hidden">
            <ServicesSectionMobile />
        </div>
    </main>
</template>

<script setup>
import HeroSection from '~/components/sections/HeroSection.vue';
import ServicesSection from '~/components/sections/ServicesSection.vue';
import HeroSectionMobile from '~/components/sections/HeroSectionMobile.vue';
import ServicesSectionMobile from '~/components/sections/ServicesSectionMobile.vue';
</script>

