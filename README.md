#5εર❡𝘼𝘿𝙎𝙄𝙕 𝙆𝘼𝙋𝙏𝘼𝙉²°๛♪⁪⁬⁮⁮⁮⁮‌‌‌‌✘ᴋɪᴢɪʟᴤᴀɴᴄᴀᴋ✘ ⁪⁬⁮⁮⁮⁮ ‌:
import time
from pyrogram import Client, filters


api_id = 1232300
api_hash = 'dce3183d468a7193a7c6518f20af08f5'
bot_token = '1733161004:AAEfs9lu6FwlrEU08wFV7pEKY9L1iQj-P60'


app = Client("pycharm",api_id=api_id , api_hash= api_hash, bot_token=bot_token)

@app.on_message(filters.command(["start"] ,["/"]))
def start(client , message):
    if message.chat.type  == 'private':
        message.reply(f"Sayın {message.from_user.first_name}\nBen Özel Sohbetler İçin Yapılmadım\nGruplara Ekleyip Mesajları Görmem İçin Boş Tag Verirseniz Sizin İçin Grup Üyelerini Etiketleyebilirim\nCreated by @ReislerSupport\nTeşekkürler İyi Günler...")

    elif message.chat.type == 'supergroup' or 'group':
        message.reply("Bot Çalışıyor...\nBotu Kullanmak İçin =  @all SAYI METİN \nCreated by @ReislerSupport")

@app.on_message(filters.private)
def ozel_mesaj(client , message):
    app.send_message(message.chat.id,f"Sayın {message.from_user.first_name}\nBen Özel Sohbetler İçin Yapılmadım\nGruplara Ekleyip Mesajları Görmem İçin Boş Tag Verirseniz Sizin İçin Grup Üyelerini Etiketleyebilirim\nCreated by @ReislerSupport\nTeşekkürler İyi Günler...")

@app.on_message(filters.command(['all'],['@']))
def all(client , message):
    if message.text.split()[1].isnumeric():
        uye_sayi = app.get_chat_members_count(message.chat.id)
        metin = ""
        sayi = int(message.text.split()[1])
        sayac = 0
        kisiler = app.get_chat_members(message.chat.id)

        if uye_sayi < sayi:
            message.reply("Girdiğiniz Sayı Grup Üye Sayısından Fazla !!")
            pass
        else:
            for i in message.text.split()[2:]:
                metin += i + ' '
            message.reply(f"{sayi} kişi etiketleniyor...\n**Sebep** : {metin}__\n**by** @ReislerSupport")

            for kisi in kisiler:

                if kisi.user.is_bot == False:
                    isim = kisi.user.first_name
                    app.send_message(message.chat.id,f"[{isim}](tg://user?id={kisi.user.id}) {metin}")
                    time.sleep(2)

                    sayac += 1
                    if sayac == sayi:
                        app.send_message(message.chat.id,f'{sayi} Kişi Etiketlendi...\nby @ReislerSupport')
                        break


    else:
        metin = ""
        for i in message.text.split()[1:]:
            metin += i + ' '
        sayi = 50
        sayac = 0
        kisiler = app.get_chat_members(message.chat.id)


        message.reply(f"Kişiler etiketleniyor...\n**Sebep** : {metin}\n**by** __@ReislerSupport")

        for kisi in kisiler:
            if kisi.user.is_bot == False:
                isim = kisi.user.first_name
                app.send_message(message.chat.id, f"[{isim}](tg://user?id={kisi.user.id}) {metin}")
                time.sleep(2)

                sayac += 1
                if sayac == sayi:
                    app.send_message(message.chat.id, f'Kişiler Etiketlendi...\nby @ReislerSupport')
                    break


app.run()

{
    "_": "Message",
    "message_id": 592,
    "from_user": {
        "_": "User",
        "id": 1617782127,
        "is_self": false,
        "is_contact": false,
        "is_mutual_contact": false,
        "is_deleted": false,
        "is_bot": false,
        "is_verified": false,
        "is_restricted": false,
        "is_scam": false,
        "is_fake": false,
        "is_support": false,
        "first_name": "Adsız Kaptan",
        "status": "recently",
        "username": " @adsizimlores ",
        "language_code": "tr",
        "dc_id": 4,
        "photo": {
            "_": "ChatPhoto",
            "small_file_id": "AQADBAADZroxGz2-8FMACK0onyddAAMCAANvZW1gAATIUy9Ey-fIzJdqBwABHgQ",
            "small_photo_unique_id": "AQADrSifJ10AA5dqBwAB",
            "big_file_id": "AQADBAADZroxGz2-8FMACK0onyddAAMDAANvZW1gAATIUy9Ey-fIzJlqBwABHgQ",

"big_photo_unique_id": "AQADrSifJ10AA5lqBwAB"
        }
    },
    "date": "2021-04-21 06:08:49",
    "chat": {
        "_": "Chat",
        "id": -1001343550284,
        "type": "supergroup",
        "is_verified": false,
        "is_restricted": false,
        "is_creator": false,
        "is_scam": false,
        "is_fake": false,
        "title": "Silinen grup",
        "permissions": {
            "_": "ChatPermissions",
            "can_send_messages": true,
            "can_send_media_messages": true,
            "can_send_stickers": true,
            "can_send_animations": false,
            "can_send_games": true,
            "can_use_inline_bots": true,
            "can_add_web_page_previews": true,
            "can_send_polls": true,
            "can_change_info": true,
            "can_invite_users": true,
            "can_pin_messages": true
        }
    },
    "mentioned": false,
    "scheduled": false,
    "from_scheduled": false,
    "text": "@all",
    "outgoing": false,
    "command": [
        "all"
    ]
}
