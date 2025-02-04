# SOUCODE ENDPOINT API

### ENDPOINT API WALPAPER AOV
```
case'aov': case 'wp-aov': {
if (usersdb[m.sender].limit < 1) return m.warning(`Limit pemakaian tercapai, chat pemilik bot agar mendapatkan limit kembali\n\n${ownnomor}`)
if (!text) return m.reply('Sertakan Nama');
vreden.sendMessage(m.chat,{
image: {url: `https://www.api.im-rerezz.xyz/api/wp-aov?text=${text}`},
caption: `*Random ${command}*`,
}, {quoted: m})
}
break
```

### ENDPOINT API GPT TURBO
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
break;
```
