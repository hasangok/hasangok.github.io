---
title: C’de Veri Tipleri
date: 2009-05-20 19:02
---

Önceki yazılarımda scanf ile klavyenizden bir tamsayı değeri okuyup bunları ekranda printf fonksiyonu ile yazdırmıştık. Dikkat ettiyseniz yaptığımız örneklerde hep %d ile tamsayıları kullandık. Peki programımızda ondalık sayılar, karakterler ya da dizgiler (string) kullanmamız gerektiği zaman ne olacak? İşte o zaman aşağıdaki tablo yardımımıza koşacak.

<!--more-->

| **Kullanım**  | **Veri Tipi**                          |
| ------------- |--------------------------------------- |
| %c            | Karakter                               |
| %d            | Tamsayı                                |
| %e            | Bilimsel gösterim (scientific notation)|
| %f , %lf      | Reel sayı                              |
| %g            | %e ve %f den kısa olanını kullanır     |
| %s            | Dizgi (string)                         |
| %u            | İşaretsiz ondalık                      |
| %x            | Hexadecimal                            |

Bu tablo tek başına bir anlam ifade etmeyeceğinden birkaç örnek program parçası yazıp olayı kavramaya çalışalım.
```c
int a=5;
double b=2.8;
printf("a=%d ve b=%f dir.",a,b);
```
Programımıza böyle bir kod dizi yazıp çalıştırdığımızda ekranda şunu göreceğiz: "**a=5 ve b=2.8 dir.**"

Sanırım ondalık sayı tanımlama ve fonksiyon içerisinde kullanma anlaşılmıştır. Bir tane de karakterler için örnek kod yazıp bu dersi kısa kesebiliriz.

```c
char karakter=’B’;
printf("%c",karakter);
```
Programımıza bu kodları yazıp çalıştırsaydık ekranda sadece B harfini görecektik. Belki ilerde işimize yarar diye bir de ipucu vereyim. Karakter örneğimizi ekrana yazdırırken %c yerine %d kullansak ne olurdu? Şu olurdu: B’nin (büyük B, küçüğü farklıdır.) ascii tablosundaki tamsayı karşılığı ekrana yazdırılırdı ve ekranda 66 sayısını görürdünüz.

Yukarıdaki tabloda en önemli veri tiplerinden biri de dizgiler (yani stringler). Burada iki satırda geçilmeyecek kadar önemli ve üzerinde durulması gereken bir konu. Onun için bu konuyu daha bilgili bir zamana erteliyorum.

Bir sonraki yazımda şu ana kadar bildiğimiz her şeyi içeren bir örnek yapıp sonrasında karşılaştırma komutlarından bahsederiz (if ile başlarız, while, do-while, for diye devam ederiz).

O zamana kadar kendinize iyi bakın. Benden ayrılmayın... 😉