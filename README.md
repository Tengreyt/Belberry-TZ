# Belberry — Тестовое задание для Frontend-разработчика

<p align="center">
  <img src="https://img.shields.io/badge/Nuxt%203-00DC82?logo=nuxtdotjs&logoColor=white&style=for-the-badge" alt="Nuxt 3"/>
  <img src="https://img.shields.io/badge/TailwindCSS-38B2AC?logo=tailwindcss&logoColor=white&style=for-the-badge" alt="TailwindCSS"/>
  <img src="https://img.shields.io/badge/Swiper-6332F6?logo=swiper&logoColor=white&style=for-the-badge" alt="Swiper"/>
  <img src="https://img.shields.io/badge/TypeScript-3178C6?logo=typescript&logoColor=white&style=for-the-badge" alt="TypeScript"/>
  <img src="https://img.shields.io/badge/Vue%203-42B883?logo=vue.js&logoColor=white&style=for-the-badge" alt="Vue 3"/>
</p>

> Сайт доступен для просмотра по адресу: [https://belberry-tz.vercel.app/](https://belberry-tz.vercel.app/)

## Описание

Это тестовый проект для frontend-разработчика, выполненный на **Nuxt 3**. В проекте реализованы:
- Адаптивный лендинг digital-агентства.
- Калькулятор стоимости сайта с динамическим расчетом суммы.
- Слайдер услуг на базе библиотеки **Swiper**.
- Единое модальное окно для заявок («Связаться» и «Заказать»), с поддержкой передачи суммы из калькулятора.
- Современный UI с использованием TailwindCSS.

---

## Техническое задание

- **Фреймворк:** Nuxt 3
- **Слайдер:** Swiper
- **Модальное окно:** Общее для кнопок «Связаться» и «Заказать». При вызове из калькулятора в модалку подставляется текст:  
  > «Мы рассчитали стоимость вашего сайта — она составила N рублей. Оставьте свои контакты, и наш менеджер свяжется с вами в ближайшее время.»  
  Сумма (N) автоматически подставляется из калькулятора.
- **Калькулятор:**
  - Опции в селекторах и их стоимость заданы произвольно.
  - Итоговая сумма рассчитывается как сумма всех выбранных пунктов.
  - Сумма отображается на странице и передается в модальное окно при отправке заявки.

---

## Project structure (hero, services, и тд.)

```
Belberry/
  ├── app.vue
  ├── assets/
  ├── components/
      ├── sections/         # hero, services, etc.
      ├── layouts/          # header, footer
      ├── ui/               # reusable UI components (buttons, inputs, modal, etc.)
      ├── icons/            # SVG icon components
      └── ...
  ├── layouts/
  ├── pages/
  ├── public/
  ├── server/
  ├── nuxt.config.ts
  ├── package.json
  ├── tailwind.config.js
  └── tsconfig.json
```

- **components/sections/** — hero, services, and other main page sections
- **components/layouts/** — layout components (header, footer)
- **components/ui/** — reusable UI components (buttons, inputs, selects, modals)
- **components/footer/** — mobile footer and modal window

---

## Калькулятор стоимости

- Находится в футере (десктоп и мобильная версия).
- Позволяет выбрать тип сайта, CMS, тематику, дизайн и дополнительные услуги.
- Каждая опция имеет свою стоимость.
- Итоговая сумма рассчитывается автоматически и отображается пользователю.
- При нажатии «Связаться с нами» открывается модальное окно с подставленной суммой.

---

## Модальное окно

- Открывается по клику на «Связаться» или «Заказать».
- Если открыто из калькулятора, в тексте модального окна отображается рассчитанная сумма.
- Форма включает поля: имя, телефон, чекбокс согласия с политикой конфиденциальности.
- После отправки формы данные можно обработать (реализация отправки — по необходимости).

---

## Слайдер услуг

- Реализован с помощью библиотеки **Swiper**.
- Адаптивен, поддерживает навигацию.
- Используется для показа карточек услуг.

---

## Установка и запуск

### 1. Установка зависимостей

```bash
npm install
# или
yarn install
# или
pnpm install
```

### 2. Запуск в режиме разработки

```bash
npm run dev
# или
yarn dev
# или
pnpm dev
```

Приложение после запуска локально будет доступно по адресу: http://localhost:3000

### 3. Сборка для продакшена

```bash
npm run build
npm run preview
```

---

## Используемые технологии

<p>
  <img src="https://img.shields.io/badge/Nuxt%203-00DC82?logo=nuxtdotjs&logoColor=white&style=for-the-badge" alt="Nuxt 3"/>
  <img src="https://img.shields.io/badge/TailwindCSS-38B2AC?logo=tailwindcss&logoColor=white&style=for-the-badge" alt="TailwindCSS"/>
  <img src="https://img.shields.io/badge/Swiper-6332F6?logo=swiper&logoColor=white&style=for-the-badge" alt="Swiper"/>
  <img src="https://img.shields.io/badge/TypeScript-3178C6?logo=typescript&logoColor=white&style=for-the-badge" alt="TypeScript"/>
  <img src="https://img.shields.io/badge/Vue%203-42B883?logo=vue.js&logoColor=white&style=for-the-badge" alt="Vue 3"/>
</p>

---

## Примечания

- Все опции калькулятора и их стоимости заданы произвольно, как указано в ТЗ.
- Проект выполнен в рамках тестового задания, без интеграции с backend.

---

## Скриншоты

1. ![Главный экран](assets/images/screenshots/Снимок%20экрана%201.png)
   
   *Главный экран сайта с HeroSection и основным предложением.*

2. ![Калькулятор стоимости](assets/images/screenshots/Снимок%20экрана%202.png)
   
   *Калькулятор стоимости сайта с выбором опций и расчетом итоговой суммы.*

3. ![Слайдер услуг](assets/images/screenshots/Снимок%20экрана%203.png)
   
   *Секция слайдера услуг, реализованного на Swiper.*

4. ![Модальное окно заявки](assets/images/screenshots/Снимок%20экрана%204.png)
   
   *Модальное окно для отправки заявки с подставленной суммой из калькулятора.*

---

## Контакты

Для связи: [email-trmv.halid@gmail.com / ТГ-@Tengreyt]
