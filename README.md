- 👋 Hi, I’m @Artike
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
Artike/Artike is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
from telegram import Update
from telegram.ext import Updater, CommandHandler, CallbackContext

# Ваш токен Telegram бота
TOKEN = "7889892017:AAENdUzgFZ6jUXRx3M4Zy1e8JvNKMcMqzM8"
TIKTOK_LINK = "https://www.tiktok.com/@nft.creator.2?_t=ZN-8slhZuya8fe&_r=1"

# Команда /start - приветственное сообщение
def start(update: Update, context: CallbackContext) -> None:
    update.message.reply_text(
        "Добро пожаловать! 🚀\n"
        "Я бот для анализа и рекомендаций товаров. Посетите наш TikTok: \n"
        f"{TIKTOK_LINK}\n\n"
        "Доступные команды:\n"
        "/tiktok - Перейти на наш TikTok\n"
        "/latest_video - Посмотреть последнее видео\n"
        "/stats - Узнать статистику TikTok\n"
        "/help - Показать список команд"
    )

# Команда /tiktok - ссылка на TikTok
def tiktok(update: Update, context: CallbackContext) -> None:
    update.message.reply_text(
        f"Следите за нашим TikTok: {TIKTOK_LINK}"
    )

# Команда /latest_video - фейковая функция для получения последнего видео (пример)
def latest_video(update: Update, context: CallbackContext) -> None:
    update.message.reply_text(
        "Последнее видео: NFT для начинающих!\n"
        f"Смотрите на TikTok: {TIKTOK_LINK}"
    )

# Команда /stats - статистика TikTok
def stats(update: Update, context: CallbackContext) -> None:
    update.message.reply_text(
        "Статистика TikTok:\n"
        "Постов: 50\n"
        "Просмотров: 150,000+\n"
        "Поклонников: Растём каждый день!"
    )

# Команда /help - помощь
def help_command(update: Update, context: CallbackContext) -> None:
    update.message.reply_text(
        "Список команд:\n"
        "/tiktok - Ссылка на TikTok\n"
        "/latest_video - Посмотреть последнее видео\n"
        "/stats - Узнать статистику TikTok\n"
        "/help - Показать список команд"
    )

# Настройка бота
def main():
    updater = Updater(TOKEN)

    # Регистрация команд
    updater.dispatcher.add_handler(CommandHandler("start", start))
    updater.dispatcher.add_handler(CommandHandler("tiktok", tiktok))
    updater.dispatcher.add_handler(CommandHandler("latest_video", latest_video))
    updater.dispatcher.add_handler(CommandHandler("stats", stats))
    updater.dispatcher.add_handler(CommandHandler("help", help_command))

    # Запуск бота
    updater.start_polling()
    updater.idle()
    #
