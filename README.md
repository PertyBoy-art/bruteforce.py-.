
   from telegram import Update
   from telegram.ext import Updater, CommandHandler, MessageHandler, Filters, CallbackContext

   # Ваш токен
   TOKEN = 'YOUR_TOKEN_HERE'

   def start(update: Update, context: CallbackContext):
       update.message.reply_text('Привет! Я бот для ловли чеков.')

   def handle_message(update: Update, context: CallbackContext):
       text = update.message.text
       # Здесь можно добавить логику обработки чеков
       if "чек" in text:
           update.message.reply_text('Чек обнаружен!')

   def main():
       updater = Updater(TOKEN)
       dp = updater.dispatcher

       dp.add_handler(CommandHandler("start", start))
       dp.add_handler(MessageHandler(Filters.text & ~Filters.command, handle_message))

       updater.start_polling()
       updater.idle()

   if __name__ == '__main__':
       main()

   
