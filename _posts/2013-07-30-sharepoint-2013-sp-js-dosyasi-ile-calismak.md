---
layout: post
title: Sharepoint 2013 SP.js Dosyası ile Çalışmak
date: 2013-07-30 15:21
author: hasangok
comments: true
Tags: [JavaScript, SharePoint, Sharepoint 2013, SP.js]
---
<p style="text-align: justify;">Javascript Object Model kullanarak, Sharepoint 2010 üzerinde listeye bağlanıp veri çekebiliyordum. Bunun için javascript kodumuzu aşağıdaki fonksiyonun içinde kullanıyorduk:</p>

<pre class="brush: js;">ExecuteOrDelayUntilScriptLoaded("javascript fonksiyonu", "sp.js");</pre>
<p style="text-align: justify;">Fakat Sharepoint 2013 üzerinde bu fonksiyon çalışmıyor. Aslında çalışıyor da, neyse o mesele çok karışık :) Yapmamız gereken değişiklik şöyle:</p>

<pre class="brush: js;">SP.SOD.executeFunc('sp.js', 'SP.ClientContext', "javascript fonksiyonu");</pre>
