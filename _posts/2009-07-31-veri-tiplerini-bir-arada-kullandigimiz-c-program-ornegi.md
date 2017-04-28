---
layout: post
title: Veri Tiplerini Bir Arada Kullandığımız C Program Örneği
date: 2009-07-31 23:13
author: hasangok
comments: true
categories: [C, C Programlama, dizgi, Programlama, veri tipi]
---
Bir önceki konumuzda kısaca hangi veri tipini hangi amaç için kullandığımızdan bahsettik. Şimdi genel bir tekrar olması açısından kullanıcıdan tamsayı, ondalık sayı, karakter ve string (dizgi, karakter dizisi) bilgileri girmesini isteyen ve bunları ekrana yazdıran bir C programı yazalım:
```c
#include<stdio.h>

int main(void)
{

    int numara=0;
    float ortalama=0;
    char harf;
    char isim[10];
    printf("Numara giriniz: ");
    scanf("%d",&amp;numara);
    printf("Isim: ");
    scanf("%s",&amp;isim);
    printf("Not ortalamasi: ");
    scanf("%f",&amp;ortalama);
    printf("Notun harf karsiligi: ");
    scanf("%c",&amp;harf);
    scanf("%c",&amp;harf);
```
/*buraya kadar kullanıcıdan sırayla bir öğrenci numarası, isim (10 karakter uzunluğunda tanımladık dikkat ederseniz), not ortalamasıve notun harf karşılığını girmesini istedik. Dikkat ettiyseniz harfkarşılığını iki kez girmesini istedik. Bunun sebebi not ortalamasındansonra "Enter"a bastığımız zaman bunu karakter olarak okuması.Şimdi bunları formatlı biçimde kullanıcıya gösteren kodları yazalım */
```c
    printf("\n\nOgrencinin:\nNumarasi: %d\n",numara);
    printf("Adi: %s\n",isim);
    printf("Not Ortalamasi: %f\n",ortalama);
    printf("Notun Harf Karsiligi: %c\n",harf);
    return 0;
}
```
Bu basit program ile de sadece tamsayılarla uğraşmaktan kurtulmuş olup karakter, ondalık sayı ve string’lerin ne şekilde kullanıldığını öğrenmiş olduk. Diğer yazımda karşılaştırma ve döngü işlemlerinin ne şekilde yapıldığından bahsedeceğim ve kullanıcıdan aldığı bilgileri geri gösteren değil, daha işlevsel programcıklar yazmaya başlayacağız.
