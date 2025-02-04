# SOUCODE ENDPOINT API

### ENDPOINT API
```
https://www.api.im-rerezz.xyz/api/wp-aov?text=${text}
```

### SOUCODE
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
