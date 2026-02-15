# Mafia Notify Bot (Telegram) — Py3.13 fixed

## Important
- BotFather: /setprivacy -> Disable
- Add bot to the group.

## Install
```powershell
python -m venv .venv
.\.venv\Scriptsctivate
python -m pip install -U pip setuptools wheel
pip install -r requirements.txt
copy .env.example .env
# edit .env (BOT_TOKEN, ADMIN_IDS)
python main.py
```

## Commands
Private:
- /start
- /players
- /subs

Group (admins only):
- reply to organizer post: /track  (or /track notify)
- /event
- /untrack

## Auto-tracking
- Теперь /track не обязателен: бот автоматически начинает отслеживать пост записи, если его отправил пользователь из ADMIN_IDS и в тексте есть блок "Список игроков" + символы ❓.
- /track остаётся как ручной override/отладка.

## .env flags (тестирование)
- REPEAT_NOTIFY=1 — повторные уведомления (игнорировать notify_log)
- NOTIFY_ON_CREATE=1 — уведомлять сразу при создании/копировании новой записи
- ANNOUNCE_AUTOTRACK=1 — писать в группу короткое сообщение, что запись взята под отслеживание


## Troubleshooting: база не наполняется
- Убедись, что в BotFather выключен privacy mode (`/setprivacy -> Disable`).
- Проверь, что бот добавлен в группу/канал и имеет права читать сообщения и edited messages.
- В `.env` задай постоянный путь к БД, например: `DB_PATH=./data/bot.db`.
- После старта проверь лог: бот выводит `DB_PATH`, по этому пути должна лежать актуальная sqlite база.
