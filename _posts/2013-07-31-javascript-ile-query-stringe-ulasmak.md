---
layout: post
title: JavaScript ile Query String'e Ulaşmak
date: 2013-07-31 11:12
author: hasangok
comments: true
Tags: [Javascript, JavaScript, Query String]
---
<p style="text-align: justify;">Bu aralar Javascript ile haşır neşir oluyorum. Hayatımda ilk kez kullandığım için her basit şey benim için yeni bir bilgi oluyor. Son çalışmamda URL'deki query string'e ulaşmam gerekiyordu. Bunu C# tarafında şu şekilde yapabildiğimizi biliyordum:</p>
<pre class="brush: c-sharp;">
string str = Page.Request.QueryString["q"];
</pre>
<p style="text-align: justify;">Ancak bunu Javascript ile yapmam gerekiyordu ki, hem her değişiklikte deploy yapmak zorunda kalmayayım hem de Javascript kodlarım kendi başına ayrı bir yerde durabilsin. Şöyle bir fonksiyon buldum işimi gören:</p>
<pre class="brush: js;">
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
</pre>
<p style="text-align: justify;">Eğer "http://www.hasangok.com.tr?q=test" şeklinde bir URL'den "test" kelimesini almak istiyorsak yukarıdaki fonksiyonu şu şekilde kullanıyoruz:</p>
<pre class="brush: js;">
var str = qs('q');
</pre>
<p style="text-align: justify;">Bilgi: "Query String de ne ola?" diyenler <a href="http://en.wikipedia.org/wiki/Query_string" target="_blank">şuraya</a> bakabilir.
Sevgiler.</p>
