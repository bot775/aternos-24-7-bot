const mineflayer = require('mineflayer');

const bot = mineflayer.createBot({
  host: 'Bidbout86562.aternos.me', // ← заміни на адресу свого Aternos-сервера
  port: 18162,
  username: 'AFK_Bot'
});

bot.on('spawn', () => {
  console.log('✅ Бот зайшов на сервер!');
  bot.chat('Привіт! Я онлайн і тримаю сервер :)');

  setInterval(() => {
    bot.setControlState('jump', true);
    setTimeout(() => bot.setControlState('jump', false), 300);
  }, 10000);
});

bot.on('error', err => console.log('❌ Помилка:', err));
bot.on('end', () => {
  console.log('🔄 Відключення. Перезапуск...');
  setTimeout(() => process.exit(), 5000);
});
