<template>
  <!-- Подключил шрифты таким оброзом, не хотел возиться сними, были баги. может это из-за моего компа(обычно так) -->
    <div class="min-h-screen flex flex-col" style="font-family: 'Golos Text', sans-serif;">
      <LayoutsHeader class="container" />
      
      <div class="flex-grow bg-[#f2f2f2eb] pb-[50px]">
        <main class="container">
            <NuxtPage />
        </main>
        
        <LayoutsFooter class="container hidden md:block" />
        <FooterMobile class="block md:hidden" />
      </div>
    </div>
</template>

<style scoped>
.container {
    max-width: 1280px;
    margin: 0 auto;
}
</style>