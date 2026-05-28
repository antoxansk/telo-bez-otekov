# HANDOFF — Тело без отёков · Лендинг-захват УПДН

> Обновлено: 2026-05-28  
> Проект: Лендинг «Тело без отёков» — захват email-лидов на 3 бесплатных видеоурока  
> Статус: **Сайт задеплоен, ожидает DNS + GetCourse URL**

---

## 1. Быстрый старт для следующей сессии

Вставь в новую сессию Claude Code:

```
Прочитай HANDOFF.md в папке /Users/mac/Desktop/УПДН/Создание сайта/
Это документ передачи контекста по проекту лендинга УПДН «Тело без отёков».

Репозиторий: https://github.com/antoxansk/telo-bez-otekov
GitHub Pages (временный URL): https://antoxansk.github.io/telo-bez-otekov
Целевой домен: https://telo.nutritionist4day.ru (CNAME ещё не прописан)

Подтверди что понял состояние проекта и приступай к задаче.
```

---

## 2. Ссылки и реквизиты

| Ресурс | Значение |
|--------|----------|
| **Репозиторий GitHub** | https://github.com/antoxansk/telo-bez-otekov |
| **GitHub аккаунт** | antoxansk |
| **GitHub Pages URL** | https://antoxansk.github.io/telo-bez-otekov |
| **Целевой домен** | https://telo.nutritionist4day.ru |
| **Файл проекта** | `/Users/mac/Desktop/УПДН/Создание сайта/index.html` |
| **Email проекта** | ai.updn@gmail.com |

---

## 3. Архитектура проекта

```
Единственный файл: index.html (431 KB)
├── <head>
│   ├── <script id="config">    ← CONFIG: formActionUrl, thankYouUrl, variants A/B, videos[]
│   ├── inline <style>          ← Весь CSS + media queries (900px, 360px)
│   └── Google Fonts link       ← Playfair Display + Geologica
└── <body>
    ├── nav.fixed               ← Логотип + кнопка «Получить уроки»
    ├── section.hero            ← A/B заголовок + карточки 3 видео + social proof
    ├── section.pain-sec        ← 6 карточек болей + цитата Шевцовой
    ├── section.vl-sec          ← 3 урока с реальными превью + описаниями
    ├── section.truth-sec       ← 7 тезисов
    ├── section.expert-sec      ← Фото Шевцовой + биография + 2 стат-карточки
    ├── section#register-form   ← Форма: name + email + чекбокс + скрытые UTM
    ├── section.faq-sec         ← 6 вопросов-аккордеон
    ├── footer                  ← © 2026 УПДН + ссылка политика ПД
    ├── .popup-ov               ← Exit-intent попап (5 сек)
    └── <script>                ← Вся логика: A/B, UTM, форма, попап, FAQ
```

**Стек:** один HTML5 файл · inline CSS · vanilla JS · без npm · без сборки  
**Хостинг:** GitHub Pages (бесплатно, без ограничений)  
**Изображения:** встроены как base64 data URI прямо в HTML

---

## 4. Что уже реализовано и задеплоено ✅

### Сайт (index.html)

| Функция | Статус | Детали |
|---------|--------|--------|
| Все 9 секций лендинга | ✅ Готово | nav, hero, pain, video-lessons, truth, expert, form, faq, footer |
| A/B тест заголовков | ✅ Готово | `?variant=a` / `?variant=b` или `?utm_content=variant_a/b` |
| Форма захвата лидов | ✅ Готово | Имя + Email + чекбокс согласия |
| Передача UTM-меток | ✅ Готово | utm_source, medium, campaign, content, term → скрытые поля |
| Поле headline_variant | ✅ Готово | Передаёт 'a' или 'b' в GetCourse |
| Honeypot (антибот) | ✅ Готово | `input[name="website"]` скрытый |
| Exit-intent попап | ✅ Готово | Через 5 сек, sessionStorage, не повторяется |
| Мобильная адаптация | ✅ Готово | Mobile-first, 360–900px, без горизонтального скролла |
| FAQ аккордеон | ✅ Готово | 6 вопросов, один открытый одновременно |
| Фото Шевцовой | ✅ Готово | ШЕВЦОВА.jpg → сжата до 71KB → встроена в HTML |
| Превью видео 1–3 | ✅ Готово | Видео №1-3.png → сжаты до ~70KB → встроены в HTML |
| Длительности уроков | ✅ Готово | Урок 1: 4 мин · Урок 2: 10 мин · Урок 3: 7 мин |
| Подзаголовок видео | ✅ Готово | «3 урока · по 9–10 минут каждый. Видео откроется сразу после регистрации.» |
| Fetch + AbortController | ✅ Готово | 10 сек timeout, CORS fallback на нативный submit |
| Guard REPLACE_ME | ✅ Готово | При сабмите без URL → alert с инструкцией |
| noindex/nofollow | ✅ Готово | Поисковики не индексируют |
| Анимации кнопок | ✅ Готово | Pulse + hover, prefers-reduced-motion |
| Плейсхолдер Я.Метрики | ✅ Готово | Комментарий в `<head>`, ym() закомментирован в JS |
| Плейсхолдер VK Pixel | ✅ Готово | Комментарий в `<head>` |

### Деплой

| Ресурс | Статус | Детали |
|--------|--------|--------|
| GitHub репозиторий | ✅ Создан | github.com/antoxansk/telo-bez-otekov, ветка main |
| GitHub Pages | ✅ Включён | Deploy from branch: main / (root) |
| CNAME файл в репо | ✅ Есть | Содержит: `telo.nutritionist4day.ru` |
| Временный URL | ✅ Работает | https://antoxansk.github.io/telo-bez-otekov |

---

## 5. Что НЕ сделано — нужно до запуска трафика ❌

### 🔴 Критично (без этого форма не работает)

#### 1. GetCourse — URL формы и страницы «спасибо»

Нужно от технического специалиста GetCourse:

- **`CONFIG.formActionUrl`** — URL для отправки лида (сейчас `"REPLACE_ME"`)  
  Формат: `https://updn.getcourse.ru/pl/lite/widget/widget/submit?id=XXXXX`

- **`CONFIG.thankYouUrl`** — URL страницы с первым видео после регистрации (сейчас `"REPLACE_ME"`)  
  Формат: `https://updn.getcourse.ru/pl/lite/...`

**Как вставить** (в index.html, строки 15–16):
```javascript
formActionUrl: "https://updn.getcourse.ru/pl/...",  // ← вставить реальный URL
thankYouUrl:   "https://updn.getcourse.ru/pl/...",  // ← вставить реальный URL
```

Поля, которые отправляются в GetCourse:
- `name` — имя пользователя
- `email` — email пользователя
- `agreement` — `"yes"`
- `utm_source`, `utm_medium`, `utm_campaign`, `utm_content`, `utm_term`
- `lead_source` — `"landing_telo_bez_otekov_v1"`
- `headline_variant` — `"a"` или `"b"`

#### 2. DNS CNAME-запись

**ТЗ для технического специалиста по домену:**

| Поле | Значение |
|------|----------|
| Тип записи | CNAME |
| Имя (Hostname) | `telo` (т.е. telo.nutritionist4day.ru) |
| Значение (Target) | `antoxansk.github.io` |
| TTL | 300 |

После добавления записи:
1. GitHub автоматически найдёт DNS (5–30 минут)
2. Выпустит SSL-сертификат Let's Encrypt (ещё 10–15 минут)
3. В настройках репо (Settings → Pages) включить **«Enforce HTTPS»**
4. Сайт откроется на `https://telo.nutritionist4day.ru`

---

### 🟡 Важно (аналитика и юридика)

#### 3. Яндекс.Метрика

1. Зайти на metrika.yandex.ru
2. Добавить счётчик для домена `telo.nutritionist4day.ru`
3. Получить ID счётчика (8 цифр, пример: `12345678`)
4. Вставить код счётчика в `index.html` вместо комментария:
   ```html
   <!-- Яндекс.Метрика: вставить счётчик сюда -->
   ```
5. В той же секции JS раскомментировать строку (примерно строка 1271):
   ```javascript
   // if (typeof ym !== 'undefined') ym(COUNTER_ID, 'reachGoal', 'form_submit');
   ```
   Заменить `COUNTER_ID` на реальный ID.
6. В Яндекс.Метрике создать цель: **«JavaScript событие»** → `form_submit`

#### 4. VK Pixel (если нужен ретаргетинг)

1. В кабинете VK Рекламы получить ID пикселя
2. Вставить код пикселя в `index.html` вместо комментария:
   ```html
   <!-- VK Pixel: вставить пиксель сюда -->
   ```

#### 5. Политика конфиденциальности

В футере ссылка `href="#"` — заменить на реальный URL политики ПД УПДН.  
Строка в HTML (примерно строка 1037):
```html
<a href="#" target="_blank" rel="noopener">Политика конфиденциальности</a>
```

---

### 🟢 Мелкие правки (не критично для запуска)

#### 6. Бейдж A/B вариантов

Сейчас написано: «3 бесплатных урока по **4–7 минут**»  
Реальные длительности: 4, 10, 7 минут — диапазон «4–10 минут».

Исправить в CONFIG (строки 22 и 29):
```javascript
badge: "3 бесплатных урока по 4–10 минут",
```

---

## 6. CONFIG — текущее состояние

```javascript
var CONFIG = {
  formActionUrl: "REPLACE_ME",          // ❌ НУЖНО ЗАМЕНИТЬ
  thankYouUrl:   "REPLACE_ME",          // ❌ НУЖНО ЗАМЕНИТЬ
  leadSource:    "landing_telo_bez_otekov_v1",  // ✅
  popupDelayMs:  5000,                  // ✅ 5 секунд

  variants: {
    a: {
      badge:       "3 бесплатных урока по 4–7 минут",   // ⚠ лучше обновить на 4–10
      h1:          "Протокол запуска лимфотока...",      // ✅
      subheadline: "Без мочегонных и их откатов...",    // ✅
      socialProof: "<strong>Уже 30 000+</strong>..."    // ✅
    },
    b: {
      badge:       "3 бесплатных урока по 4–7 минут",   // ⚠ лучше обновить на 4–10
      h1:          "Как убрать отёки лица за 7 дней...",// ✅
      subheadline: "Без мочегонных, без строгих диет...",// ✅
      socialProof: "<strong>30 000+</strong>..."        // ✅
    }
  },

  videos: [
    { duration: "4 мин",  title: "Одна идея, которую вам, скорее всего, никто не говорил", image: [data URI ~95KB] },
    { duration: "10 мин", title: "Утренний протокол на 5 минут — делаем вместе прямо сейчас", image: [data URI ~95KB] },
    { duration: "7 мин",  title: "Два скрытых фактора — почему отёки не уходят...", image: [data URI ~90KB] }
  ]
};
```

---

## 7. Файловая структура проекта

```
/Users/mac/Desktop/УПДН/Создание сайта/
├── index.html          ← Главный файл (431 KB, всё встроено)
├── HANDOFF.md          ← Этот документ
├── CLAUDE.md           ← Правила для Claude Code
├── SPEC (1).md         ← Техническое задание (источник истины)
├── PROJECT_IDEA (2).md ← Описание проекта и ЦА
├── Видео №1.png        ← Оригинал скриншота урока 1 (1.7 MB)
├── Видео №2.png        ← Оригинал скриншота урока 2 (1.9 MB)
├── Видео №3.png        ← Оригинал скриншота урока 3 (2.0 MB)
└── ШЕВЦОВА.jpg         ← Фото Татьяны Шевцовой (68 KB)

GitHub репозиторий: github.com/antoxansk/telo-bez-otekov
├── index.html          ← Задеплоено (с встроенными сжатыми изображениями)
└── CNAME               ← telo.nutritionist4day.ru
```

---

## 8. Чеклист перед запуском трафика

- [ ] Получить `formActionUrl` от GetCourse-специалиста → вставить в CONFIG
- [ ] Получить `thankYouUrl` от GetCourse-специалиста → вставить в CONFIG
- [ ] Отправить тестовый лид → проверить в GetCourse (имя, email, UTM, headline_variant)
- [ ] Проверить редирект на страницу с первым видео после сабмита
- [ ] Добавить CNAME-запись (`telo → antoxansk.github.io`) в DNS nutritionist4day.ru
- [ ] Дождаться DNS (до 30 мин) → включить «Enforce HTTPS» в GitHub Pages настройках
- [ ] Создать счётчик Я.Метрики → вставить код → добавить цель `form_submit`
- [ ] Вставить VK Pixel (если нужен)
- [ ] Заменить `href="#"` в футере на ссылку на политику конфиденциальности
- [ ] Проверить `?variant=a` и `?variant=b` на мобильном устройстве
- [ ] Проверить попап (подождать 5 сек после открытия)
- [ ] Проверить UTM-передачу: открыть `?utm_source=test&utm_campaign=test` → сабмит → смотреть в GetCourse

---

## 9. Как вносить изменения в сайт

Все правки вносятся в **один файл** — `index.html` на локальном Mac.  
После правки загружается в GitHub — Pages автоматически пересобирается за 1–2 минуты.

**Через Claude Code** (рекомендуется):
```
Открой /Users/mac/Desktop/УПДН/Создание сайта/index.html
Внеси такое-то изменение
Обнови файл в GitHub репозитории antoxansk/telo-bez-otekov
```

**Вручную через GitHub UI:**
1. Зайти на github.com/antoxansk/telo-bez-otekov
2. Нажать на `index.html` → карандаш (Edit)
3. Внести изменение → Commit changes

---

## 10. Технические детали интеграции

### Как работает форма
1. Пользователь заполняет имя + email → нажимает кнопку
2. JS валидирует (имя ≥ 2 символа, email по регулярному выражению, чекбокс отмечен)
3. Honeypot проверка (если бот заполнил скрытое поле — тихо блокируем)
4. `fetch()` с `AbortController` (таймаут 10 сек) → POST на `CONFIG.formActionUrl`
5. **Статус 200** → `window.location.href = CONFIG.thankYouUrl`
6. **CORS-ошибка** → fallback: нативный `<form>` submit (работает всегда)
7. **Таймаут / 4xx / 5xx** → показываем inline ошибку, кнопка разблокируется

### A/B логика
- `?variant=b` → вариант B (любое значение с 'b' → B, иначе A)
- `?utm_content=variant_b` → тоже вариант B
- Приоритет: `variant=` > `utm_content=`
- Без параметров → вариант A

### Попап
- Срабатывает через 5000 мс после загрузки страницы
- Не показывается если: форма уже отправлена (`sessionStorage.form_submitted`) или попап уже закрывали (`sessionStorage.popup_dismissed`)
- Кнопка в попапе → плавный скролл к форме + анимация подсветки

---

## 11. Внешние сервисы

| Сервис | Роль | Статус | Где |
|--------|------|--------|-----|
| **GitHub** | Репозиторий + хостинг (Pages) | ✅ Работает | github.com/antoxansk/telo-bez-otekov |
| **GetCourse** | Приём лидов + страница с видео | ❌ URL не настроен | updn.getcourse.ru (у тех. специалиста) |
| **Яндекс.Метрика** | Аналитика + цель form_submit | ❌ Не вставлен | metrika.yandex.ru |
| **VK Pixel** | Ретаргетинг (опционально) | ❌ Не вставлен | vk.com/ads |
| **DNS nutritionist4day.ru** | CNAME telo → GitHub Pages | ❌ Не добавлен | у тех. специалиста домена |
