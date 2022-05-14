import telebot
from telebot import types
bot = telebot.TeleBot('5300865628:AAEVwVk5b1lwzwTGUAktk008eQG-tfHkFzc')
# Функция, обрабатывающая команду /start
@bot.message_handler(commands = ["start"])
def start(message):
# пишем стандартную клавиатуру
    markup = types.ReplyKeyboardMarkup(resize_keyboard = True)
    item1 = types.KeyboardButton('Да')
    item2 = types.KeyboardButton('Нет')
    markup.add(item1,item2) # прикрепляем к клавиатуре две кнопки
    bot.send_message(message.chat.id, 'Привет! Хочешь послушать сказку?', format(message.from_user), reply_markup = markup) # прикрепляем клавиатуру к сообщению
    #функция, отслеживающая нажатие кнопок (оброботчик событий)
@bot.message_handler(content_types=['text'])
def bot_message(message):
    if message.chat.type == 'private': #личное сообщение
        if message.text == 'Да':
            markup = types.ReplyKeyboardMarkup(resize_keyboard = True)
            item3 = types.KeyboardButton('Свою')
            item4 = types.KeyboardButton('Из библиотеки')
            markup.add(item3,item4)
            bot.send_message(message.chat.id, 'Хочешь загрузить свою сказку или послушать из библиотеки?', reply_markup = markup)
        elif message.text == 'Свою':
            bot.send_message(message.chat.id, 'Пришлите мне текст сказки в сообщении')  
# далее - список кнопок со сказками и их аудиофайлами. Пока пишу их просто номерами (1,2,3...,10)            
        elif message.text == 'Из библиотеки':
# прописываем библиотеку сказок
            bot.send_message(message.chat.id, 'Выберите сказку из списка') 
            markup = types.ReplyKeyboardMarkup(resize_keyboard = True)
            item5 = types.KeyboardButton('1')
            item6 = types.KeyboardButton('2')
            item7 = types.KeyboardButton('3')
            item8 = types.KeyboardButton('4')
            item9 = types.KeyboardButton('5')
            item10 = types.KeyboardButton('6')
            item11 = types.KeyboardButton('7')
            item12 = types.KeyboardButton('8')
            item13 = types.KeyboardButton('9')
            item14 = types.KeyboardButton('10')
            markup.add(item5, item6, item7 ,item8, item9, item10, item11, item12, item13, item14)
            bot.send_message(message.chat.id, 'Выберите сказку из списка', reply_markup = markup)
  # скорость
        elif message.text == '1' or '2' or '3' or '4' or '5' or '6' or '7' or '8' or '9' or '9' or 'Пришлите мне текст сказки в сообщении':
            markup = types.ReplyKeyboardMarkup(resize_keyboard = True)
            item15 = types.KeyboardButton('1x')
            item16 = types.KeyboardButton('2x')
            item17 = types.KeyboardButton('3x')
            markup.add(item15,item16, item17)
            bot.send_message(message.chat.id, 'Выберите скорость, с которой вы хотите прослушать сказку',  reply_markup = markup)
   # голос
        elif message.text == '1x' or '2x' or '3x':
            markup = types.ReplyKeyboardMarkup(resize_keyboard = True)
            item18 = types.KeyboardButton('Женский голос')
            item19 = types.KeyboardButton('Мужской голос')
            markup.add(item18,item19)
            bot.send_message(message.chat.id, 'Выберите голос, который будет читать сказку',  reply_markup = markup)
# файл + прописать прогу, которая будет кидать файл
        elif message.text == 'Мужской голос' or 'Женский голос':
            bot.send_message(message.chat.id, 'Вот ваш файл)')
 # возвращение назад
        elif message.text == 'Вот ваш файл)':
            markup = types.ReplyKeyboardMarkup(resize_keyboard = True)
            item1 = types.KeyboardButton('Да')
            item2 = types.KeyboardButton('Нет')
            markup.add(item1,item2)
            bot.send_message(message.chat.id, 'Привет! Хочешь послушать сказку?', reply_markup = markup)

# часть, где человек вначале отвечает, что не хочет слушать сказку            
        elif message.text == 'Нет':
            markup = types.ReplyKeyboardMarkup(resize_keyboard = True)
            item20 = types.KeyboardButton('Да, я не хочу слушать ваши сказки')
            item21 = types.KeyboardButton('Я передумал(а). Хочу послушать сказку!')
            markup.add(item20, item21)
            bot.send_message(message.chat.id, 'Точно?',  reply_markup = markup)
        elif message.text == 'Я передумал(а). Хочу послушать сказку!':
            markup = types.ReplyKeyboardMarkup(resize_keyboard = True)
            item1 = types.KeyboardButton('Да')
            item2 = types.KeyboardButton('Нет')
            markup.add(item1,item2)
            bot.send_message(message.chat.id, 'Я передумал(а). Хочу послушать сказку!', reply_markup = markup)
        elif message.text == 'Да, я не хочу слушать ваши сказки':
            bot.send_message(message.chat.id, 'Пока')
                
bot.polling(none_stop=True)
