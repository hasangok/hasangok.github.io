---
title: C'de "switch-case" Yapısı
date: 2009-10-20 22:51
---

Geçen yazıda if ile karşılaştırma yapmayı öğrenmiştik. Şimdi de if komutuna bir alternatif olan switch yapısını inceleyeceğiz.

<!--more-->
switch komutu ile birlikte kullandığımız üç özel kelime daha var: case, default ve break. Şimdi bu üç kelimenin ne işe yaradığına bakalım. Okuduğumuz bir değişkeni karşılaştıracağımız seçenekleri "case" yapısını kullanarak belirleriz. "break" ile switch karşılaştırmasını bırakıp programımızın kaldığı yerden devam etmesini sağlarız. "default" ise adı üstünde varsayılan değer belirler. Eğer karşılaştırma yaptığımız değer "case"lerden birinde karşılık bulamazsa "default" ile belirlediğiniz yerden program akışı devam eder.

Şimdi bunların hepsini örnek bir program parçasında ile görelim. "sinif" adlı bir değişkenimiz olsun ve programımız girdiğimiz değere göre hangi sınıfı seçtiğimizi bize söylesin.
```c
.
.
scanf("%d",&sinif);
switch(sinif)
{
case 1: printf("Birinci sinif secildi\n");
	break;
case 2: printf("Ikinci sinif secildi\n");
	break;
case 3: printf("Ucuncu sinif secildi\n");
	break;
case 4: printf("Dorduncu sinif secildi\n");
	break;
default: printf("Yanlis secim yaptiniz\n");
}
.
.
.
```
Kodlarımıza şöyle bir bakalım ve ne yaptığını anlamaya çalışalım. Öncelikle "sinif" adlı değişkene klavyeden değer okuduk. Bu değerin 4 girildiğini varsayalım. Bu durumda "case 4:" şeklinde belirttiğimiz yerdeki kodlar çalışacak, yani ekrana "Dorduncu sinif secildi" yazacak ve "break;" ile switch yapısından çıkacak. Eğer "sinif" değişkenine "case" ile belirtmediğimiz bir değer girilirse –mesela 5- bu kez ekrana "default" ile belirlediğimiz "Yanlis secim yaptiniz" yazısı gönderilecek.

switch komutunda case değerleri boş bırakılabilir. Şöyle ki:
```c
.
.
scanf("%d",&amp;x);
switch(x)
{
case 1:
case 2:
case 3:
case 4: printf("switch burada bitiyor");
	break;
}
.
.
.
```
şeklinde bir kod parçamız varsa ve x değerine 1,2 veya 3 girildiyse yine de gidip "case 4:" ile belirtilen işlem gerçekleştirilir. Sebebi şudur: case 1, case 2 ve case 3 bölümlerinde herhangi bir işlem tanımlanmamıştır ve "break;" komutu ile switch sonlandırılmadığı için, programımız "break;" ile karşılaşıncaya dek case işlemlerini sırayla yürütür. Bu yüzden karşılaştırma işlemimiz sona erdiğinde ve switch ile işimiz bittiğinde mutlaka "break;" ile switch'in içinden çıkılmalıdır.

switch yapısını da öğrendik. Sıra geldi (sonunda 🙂) döngülere. Konuyla ilgili bir sonraki yazıda while, do-while ve for döngülerinden bahsedeceğim.
Esen kalın 🙂
