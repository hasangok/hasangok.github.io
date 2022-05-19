---
title: Sharepoint 2013 SP.js Dosyası ile Çalışmak
date: 2013-07-30 15:21
---

Javascript Object Model kullanarak, Sharepoint 2010 üzerinde listeye bağlanıp veri çekebiliyordum. Bunun için javascript kodumuzu aşağıdaki fonksiyonun içinde kullanıyorduk:

<!--more-->
```javascript
ExecuteOrDelayUntilScriptLoaded("javascript fonksiyonu", "sp.js");
```
Fakat Sharepoint 2013 üzerinde bu fonksiyon çalışmıyor. Aslında çalışıyor da, neyse o mesele çok karışık 🙂 Yapmamız gereken değişiklik şöyle:
```javascript
SP.SOD.executeFunc('sp.js', 'SP.ClientContext', "javascript fonksiyonu");
```