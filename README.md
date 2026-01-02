# public-apis
WhatsApp bot 
const { Client, LocalAuth } = require('whatsapp-web.js');
const qrcode = require('qrcode-terminal');

const client = new Client({
    authStrategy: new LocalAuth()  // Sauvegarde la session pour ne pas rescanner le QR à chaque fois
});

client.on('qr', qr => {
    qrcode.generate(qr, {small: true});  // Affiche le QR dans le terminal
    console.log('Scanne ce QR avec ton WhatsApp (Lier appareil)');
});

client.on('ready', () => {
    console.log('Bot prêt !');
});

client.on('message', async message => {
    if (message.body === '!ping') {
        message.reply('Pong !');
    } else if (message.body.toLowerCase().includes('salut')) {
        message.reply('Salut ! Comment ça va ?');
    }
     message.link('https://linktr.ee/z3rox21');

client.initialize();
