# Cursor Logs

## [2026-04-26 12:00] - Integrate Supabase Waitlist Auth

**Problem/Request:**
Необходимо привязать проект к базе данных Supabase и настроить письмо подтверждения для листа ожидания (без создания паролей).

**Files Modified:**
- draftly.html - Подключен Supabase SDK (supabase-js), заменена заглушка `submitWaitlist` на реальный вызов `signInWithOtp` и добавлена функция `handleReturn` для сохранения пользователя в таблицу `waitlist` при переходе по ссылке.

**Solution Summary:**
Использован Supabase Auth Magic Link (`signInWithOtp`). При вводе email пользователь получает письмо-ссылку. После перехода по ссылке с параметром `?confirmed=1`, фронтенд проверяет сессию и выполняет `upsert` в таблицу `waitlist`.

**Verification:**
Код добавлен в HTML и готов к тестированию на стороне клиента. В Supabase уже создана таблица `waitlist`.

**Outcome:**
✅ Success

## [2026-04-26 12:15] - Fix Vercel 404 & Add Success Modal

**Problem/Request:**
Устранить ошибку 404 при деплое на Vercel и добавить красивое модальное окно вместо alert().

**Files Modified:**
- index.html (переименован из draftly.html) - Добавлен HTML/CSS модального окна, переписана функция `handleReturn`.

**Solution Summary:**
Файл переименован в `index.html`, так как Vercel (и другие хостинги) по умолчанию ищут именно этот файл для отображения главной страницы. Также системный `alert()` заменен на стилизованное модальное окно (successModal), которое появляется при успешном подтверждении почты.

**Verification:**
Локально протестировано переименование.

**Outcome:**
✅ Success
