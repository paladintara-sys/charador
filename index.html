import logging
from telegram import Update, InlineKeyboardButton, InlineKeyboardMarkup
from telegram.ext import Application, CommandHandler, CallbackQueryHandler, ContextTypes

# Настройка логирования
logging.basicConfig(format='%(asctime)s - %(name)s - %(levelname)s - %(message)s', level=logging.INFO)

# Токен вашего бота (получите у @BotFather)
TOKEN = "ВАШ_ТЕЛЕГРАМ_ТОКЕН"

# Константы состояний игры
CHOOSE_HERO, CHAPTER_1 = range(2)

async def start(update: Update, context: ContextTypes.DEFAULT_TYPE):
    """Начало игры и выбор персонажа."""
    user = update.effective_user
    context.user_data.clear() # Сброс прогресса
    context.user_data['health'] = 100
    context.user_data['chapter'] = 1
    
    welcome_text = (
        f"Приветствую, {user.first_name}! 👋\n\n"
        "Мир Чарадора погружается во Тьму Калта. Смерги уже у границ Дремуша.\n"
        "Ты — дрёма ростом всего 30 см. Твой выбор определит судьбу Огнесада.\n\n"
        "**Кем ты встретишь этот ужас?**"
    )
    
    keyboard = [
        [InlineKeyboardButton("🎶 Дрыхала (Флейта Латар)", callback_query_data='hero_dryhala')],
        [InlineKeyboardButton("🍯 Бермяш (Волшебный Котел)", callback_query_data='hero_bermyash')]
    ]
    reply_markup = InlineKeyboardMarkup(keyboard)
    
    await update.message.reply_text(welcome_text, reply_markup=reply_markup, parse_mode='Markdown')

async def handle_choice(update: Update, context: ContextTypes.DEFAULT_TYPE):
    """Обработка всех нажатий кнопок."""
    query = update.callback_query
    await query.answer()
    
    data = query.data
    health = context.user_data.get('health', 100)
    
    # Логика выбора героя
    if data.startswith('hero_'):
        hero_type = "Дрыхала" if data == 'hero_dryhala' else "Бермяш"
        context.user_data['hero'] = hero_type
        context.user_data['inventory'] = "Латар" if data == 'hero_dryhala' else "Котел"
        
        text = (
            f"✨ Ты выбрал путь **{hero_type}**.\n\n"
            "**Глава 1: Тень на террасе**\n"
            "Луна внезапно гаснет, словно залитая чернилами. Твой чай покрывается коркой льда. "
            "Из тумана у реки Чаруши выплывают Смерги — безликие башни из копоти. "
            "Холод Калта обжигает твою кожу.\n\n"
            "Что ты сделаешь?"
        )
        
        keyboard = [
            [InlineKeyboardButton("🔥 Использовать магию Фа (-10% Искры)", callback_query_data='c1_magic')],
            [InlineKeyboardButton("🏃 Спрятаться за корнями Мирина", callback_query_data='c1_hide')]
        ]
        
    # Логика Главы 1
    elif data.startswith('c1_'):
        if data == 'c1_magic':
            health -= 10
            action_text = "Ты направляешь свет Фа против теней! Смерги шипят и отступают, но это стоило тебе сил."
        else:
            action_text = "Ты ныряешь в глубокую нору. Тень проходит мимо, но страх сковывает твое сердце."
        
        context.user_data['health'] = health
        text = (
            f"{action_text}\n\n"
            "**Глава 2: Плюшки под пеплом**\n"
            "Тьма поглотила твой дом. Ты видишь, как на столе догорают любимые плюшки, превращаясь в прах. "
            "Нужно уходить, пока мост через ручей не исчез в тумане."
        )
        keyboard = [[InlineKeyboardButton("Вперед к ручью", callback_query_data='c2_start')]]

    # Обновление статуса
    context.user_data['health'] = health
    status_line = (
        f"\n\n---\n👤 {context.user_data['hero']} | "
        f"⚡ Искра: {health}% | "
        f"📖 Глава: {context.user_data['chapter']}/10"
    )
    
    await query.edit_message_text(text + status_line, reply_markup=InlineKeyboardMarkup(keyboard), parse_mode='Markdown')

def main():
    """Запуск бота."""
    application = Application.builder().token(TOKEN).build()

    application.add_handler(CommandHandler("start", start))
    application.add_handler(CallbackQueryHandler(handle_choice))

    print("Бот запущен. Нажмите Ctrl+C для остановки.")
    application.run_polling()

if __name__ == '__main__':
    main()
