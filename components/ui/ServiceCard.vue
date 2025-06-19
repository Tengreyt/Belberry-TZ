<template>
  <div class="w-[413px] h-[400px] bg-white rounded-[20px] p-[30px] shadow-md flex flex-col justify-between">
    <h3 class="font-['Golos_Text'] h-[106px] font-medium text-[44px] leading-[100%] tracking-[0%] text-gradient-purple mb-4 whitespace-normal" v-html="title"></h3>
    <p class="font-sans font-normal text-[20px] leading-[140%] text-[#313131]" v-html="description"></p>
  </div>
</template>

<script setup>
defineProps({
  title: {
    type: String,
    required: true
  },
  description: {
    type: String,
    required: true
  }
})
</script>

<style scoped>
.text-gradient-purple {
  background-image: linear-gradient(to bottom, #0804A1, #9278FA);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  color: transparent;
}
</style> 