const TelegramBot = require('node-telegram-bot-api');
const token = process.env.BOT_TOKEN;
const channel = process.env.CHANNEL_ID;
const bot = new TelegramBot(token, { polling: true });

bot.onText(/\/start (.+)/, (msg, match) => {
  const chatId = msg.chat.id;
  const code = match[1];

  if (code === 'clip42') {
    bot.sendMessage(chatId, "🔞 این همون چیزیه که دنبالش بودی...").then((sent) => {
      setTimeout(() => {
        bot.deleteMessage(chatId, sent.message_id);
      }, 60000); // حذف بعد از ۶۰ ثانیه
    });
  }
});
