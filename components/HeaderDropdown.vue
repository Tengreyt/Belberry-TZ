<template>
  <ul :class="[isNested ? 'absolute left-full top-[-4px] mt-0 ml-0' : 'relative']"
    class="bg-white shadow-lg rounded-lg py-2 w-max min-w-[280px]"
  >
    <li v-for="item in items" :key="item.title" class="relative group">
      <NuxtLink
        v-if="!item.isDropdown"
        :to="item.to"
        class="block px-4 py-2 text-neutral-800 hover:bg-neutral-100 rounded-md transition font-sans"
      >
        {{ item.title }}
      </NuxtLink>

      <div
        v-else
        class="flex items-center justify-between px-4 py-2 text-neutral-800 hover:bg-neutral-100 rounded-md transition cursor-pointer font-sans"
        @mouseenter="handleMouseEnter(item)"
        @mouseleave="handleMouseLeave()"
      >
        <span>{{ item.title }}</span>
        <IconChevronSmall class="transform transition-transform duration-300 group-hover:rotate-90" />
      </div>

      <transition name="fade">
        <div
          v-if="item.isDropdown && activeNestedDropdown === item.title"
          class="absolute left-full top-[-4px] ml-0 z-50"
        >
          <HeaderDropdown :items="item.children" :is-nested="true" />
        </div>
      </transition>
    </li>
  </ul>
</template>

<script setup>
import { ref } from 'vue';
import IconChevronSmall from '~/components/icons/IconChevronSmall.vue';

const props = defineProps({
  items: {
    type: Array,
    required: true,
  },
  isNested: {
    type: Boolean,
    default: false,
  }
});

const activeNestedDropdown = ref(null);

const handleMouseEnter = (item) => {
  if (item.isDropdown) {
    activeNestedDropdown.value = item.title;
  }
};

const handleMouseLeave = () => {
  activeNestedDropdown.value = null;
};
</script>

<style scoped>
/* Дополнительные стили для анимаций и позиционирования */
.fade-enter-active, .fade-leave-active {
  transition: opacity 0.2s, transform 0.2s;
}
.fade-enter-from, .fade-leave-to {
  opacity: 0;
  transform: translateX(-5px);
}
.fade-enter-to, .fade-leave-from {
  opacity: 1;
  transform: translateX(0);
}

/* Убираем отступы у последнего элемента вложенного меню */
ul > li:last-child > div {
  margin-bottom: 0;
}

/* Добавляем отступы между пунктами меню */
ul > li {
  margin-bottom: 2px;
}

ul > li:last-child {
  margin-bottom: 0;
}

/* Улучшаем стили при наведении */
ul > li > div:hover,
ul > li > a:hover {
  background-color: #f3f4f6;
}
</style> 