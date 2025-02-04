# SOUCODE ENDPOINT API

### CODE SEARCH APPLE
```
case 'searchapple': {
    if (!text) return m.reply('Masukkan kata kunci yang ingin dicari.\nContoh: .searchapple Mendua');
    const apiUrl = `https://www.api.im-rerezz.xyz/api/apple-search?query=${encodeURIComponent(text)}`;

    try {
        const response = await axios.get(apiUrl);
        if (response.data.status === true) {
            const results = response.data.data;
            if (results.length === 0) {
                return m.reply('Tidak ditemukan hasil untuk pencarian tersebut.');
            }
            let message = `🔎 *Hasil Pencarian untuk "${text}":*\n\n`;
            results.forEach((item, index) => {
                message += `${index + 1}. *${item.title}*\n`;
                message += `   _${item.subtitle}_\n`;
                message += `   [Link](${item.link})\n\n`;
            });
            return m.reply(message);
        } else {
            return m.reply(`Error: ${response.data.message}`);
        }
    } catch (error) {
        console.error('Error while searching Apple Music:', error);
        return m.reply('Terjadi kesalahan saat mencari di Apple Music. Silakan coba lagi nanti.');
    }
}
break
```

### SOURCE APPLE DL
```
case 'appledl': {
    if (!text) return m.reply('Masukkan URL Apple Music yang ingin diunduh.\nContoh: .appledl https://music.apple.com/us/album/mendua/739624760?i=739624791');
    const apiUrl = `https://www.api.im-rerezz.xyz/api/appledl?url=${encodeURIComponent(text)}`;
    try {
        const response = await axios.get(apiUrl);
        if (response.data.success) {
            const data = response.data.data;
            // Kirim informasi lagu
            let infoMessage = `🎵 *Judul:* ${data.name}\n`;
            infoMessage += `💽 *Album:* ${data.albumname}\n`;
            infoMessage += `🎤 *Artis:* ${data.artist}\n`;
            infoMessage += `⏱ *Durasi:* ${data.duration}\n`;
            infoMessage += `🔗 [Apple Music Link](${data.url})`;
            await conn.sendMessage(m.chat, { image: { url: data.thumb }, caption: infoMessage }, { quoted: m });
            // Kirim file audio
            await conn.sendMessage(m.chat, { audio: { url: data.download }, mimetype: 'audio/mp4', fileName: `${data.name} - ${data.artist}.m4a` }, { quoted: m });
        } else {
            return m.reply(`Error: ${response.data.message}`);
        }
    } catch (error) {
        console.error('Error while downloading from Apple Music:', error);
        return m.reply('Terjadi kesalahan saat mengunduh lagu dari Apple Music. Silakan coba lagi nanti.');
    }
}
break
```

### SOURCODE API GPT TURBO
```
case 'gpt': {
    if (!text) return m.reply('Masukkan pesan yang ingin dikirim ke GPT.\nContoh: .gpt Halo, apa kabar?');
    const apiUrl = `https://www.api.im-rerezz.xyz/api/gptturbo?message=${encodeURIComponent(text)}`;
    try {
        const response = await axios.get(apiUrl);
        if (response.data.status === 200) {
            const gptReply = response.data.data.response;
            return m.reply(`🤖 GPT: ${gptReply}`);
        } else {
            return m.reply(`Error: ${response.data.message}`);
        }
    } catch (error) {
        console.error('Error while contacting GPT API:', error);
        return m.reply('Terjadi kesalahan saat menghubungi GPT API. Silakan coba lagi nanti.');
    }
}
break
```


