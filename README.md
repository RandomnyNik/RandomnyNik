import telebot
import secret
import json
import requests
from bs4 import BeautifulSoup as bs

fruts = ['а', 'б', 'в', 'г', 'д', 'е', 'ё', 'ж', 'з', 'и', 'й', 'к', 'л', 'м', 'н', 'о', 'п', 'р', 'с', 'т', 'у', 'ф', 'х', 'ц', 'ч', 'ш', 'щ', 'ъ', 'ы','ь', "э", "ю", "я"]
bot = telebot.TeleBot(secret.token_n1)

r = requests.get( "https://ru.wikipedia.org/wiki/%D0%9A%D0%B0%D1%82%D0%B5%D0%B3%D0%BE%D1%80%D0%B8%D1%8F:%D0%A4%D1%80%D1%83%D0%BA%D1%82%D1%8B").text
soup = bs(r, 'lxml')

@bot.message_handler(content_types=['text'])
def answer(msg):
    global text
    print('Полученно сообщение от пользователя: ', msg.from_user.id, msg.text)
    text = msg.text
    if text == "хочу фрукты на букву а" or text == "следующее" or text == "предыдущее":
        if text == "хочу фрукты на букву а":
            a = soup.findAll("div", {"class": "mw-category-group"})
           # bot.send_message(msg.from_user.id,"")

            print(a, fruts_a)
bot.polling(none_stop=True)
