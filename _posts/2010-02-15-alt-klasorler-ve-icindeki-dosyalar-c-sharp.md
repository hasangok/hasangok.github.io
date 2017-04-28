---
layout: post
title: Alt Klasörler ve İçindeki Dosyalar (C#)
date: 2010-02-15 23:48
author: hasangok
comments: true
categories: [altklasörler, C#, tüm dosyalara ulaşma]
---
Laf olsun, zaman geçsin, elim alışsın, gözüm aşina olsun, kulağım dolsun gibi amaçlarla **Klasör Eşitleyici** diye bir program yazıyorum. Piyasada tonla örneği olsa da "terzi kendi söküğünü diksin!" bu sefer dedim, kendim yazıp kendim kullanayım istedim.

Programın yapacağı iş basit: Yolunu verdiğimiz iki klasörün içeriğini karşılaştırıp birinde olup diğerinde olmayan dosyaları gerekli yerlere kopyalayıp iki klasörün içeriğini eşitleyecek. Mantık basit ama koda dökerken biraz tıkandım, rekürsif metot kullanmamaya karar verdim. Onun yerine becerikli bulduğum bir metodun tek satırlık örneğini sizlerle de paylaşmak istedim: (rahat görebilmek için ![code](http://www.hasangok.com.tr/styles/page_white_code.png) 'e tıklayınız)

```csharp
string[] dosyalar = Directory.GetFiles(@"C:\KlasörYolu\","*", SearchOption.AllDirectories);
```
KlasörYolu ile belirtilen klasördeki ve tüm altklasörlerdeki dosyaları bir string dizisine çekebiliyoruz bu şekilde. Tabi bu metodu kullanabilmek için "***using System.IO;***" da eklememiz gerek. Eğer dosyaları değil de altklasörlerin listesini almak isteseydik:
```csharp
string[] klasorler = Directory.GetDirectories(@"C:\KlasörYolu\","*", SearchOption.AllDirectories);
```
şeklinde kullanabilirdik. Benim işimi gördü, gün gelir sizinkini de görür diye buraya not ettim ;)

Hepinize kolay gelsin...
