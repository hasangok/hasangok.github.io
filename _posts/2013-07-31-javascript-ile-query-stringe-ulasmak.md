---
layout: post
title: JavaScript ile Query String'e Ulaşmak
date: 2013-07-31 11:12
author: hasangok
comments: true
Tags: [Javascript, JavaScript, Query String]
---
Bu aralar Javascript ile haşır neşir oluyorum. Hayatımda ilk kez kullandığım için her basit şey benim için yeni bir bilgi oluyor. Son çalışmamda URL'deki query string'e ulaşmam gerekiyordu. Bunu C# tarafında şu şekilde yapabildiğimizi biliyordum:
```csharp
string str = Page.Request.QueryString["q"];
```
Ancak bunu Javascript ile yapmam gerekiyordu ki, hem her değişiklikte deploy yapmak zorunda kalmayayım hem de Javascript kodlarım kendi başına ayrı bir yerde durabilsin. Şöyle bir fonksiyon buldum işimi gören:
```javascript
function qs(key) {
    var vars = [], hash;
    var hashes = window.location.href.slice(window.location.href.indexOf('?') + 1).split('&');
    for(var i = 0; i < hashes.length; i++)
    {
        hash = hashes[i].split('=');
        vars.push(hash[0]);
        vars[hash[0]] = hash[1];
    }
    return vars[key];
}
```
Eğer "http://www.hasangok.com.tr?q=test" şeklinde bir URL'den "test" kelimesini almak istiyorsak yukarıdaki fonksiyonu şu şekilde kullanıyoruz:
```javascript
var str = qs('q');
```
Bilgi: "Query String de ne ola?" diyenler [şuraya](http://en.wikipedia.org/wiki/Query_string) bakabilir.
Sevgiler.
