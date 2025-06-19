<template>
  <button
    class="
      relative overflow-hidden   /* нужно, чтобы псевдо‑элемент не выходил за границы */
      w-full py-[20px] rounded-[30px]
      text-white text-[18px] font-[600] leading-[140%]
      bg-gradient-to-r from-[#9278FA] to-[#0804A1]  /* базовый градиент */
      cursor-pointer
    "
  >
    <span class="relative z-10"><slot /></span>

    <!-- верхний слой с обратным градиентом -->
    <span
      class="
        before:content-[''] before:absolute before:inset-0
        before:bg-gradient-to-r before:from-[#0804A1] before:to-[#9278FA]
        before:opacity-0 hover:before:opacity-100
        before:transition-opacity before:duration-300 before:ease-in-out
        absolute inset-0   /* позиционируем сам span, чтобы он занимал всю кнопку */
      "
    />
  </button>
</template>
