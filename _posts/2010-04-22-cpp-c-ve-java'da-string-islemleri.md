---
title: C++, C# ve Java'da String İşlemleri
date: 2010-04-22 00:40
---

**String Tanımlama ve Atama**

Java ve C# dillerinde stringler referans veri tipi olarak tanımlıdır. C++'da ise stringler karakter dizisi olmak zorundadır. C++'da string.h kütüphanesi yardımı ile stringler, sınıflardan türeyen nesneler olarak oluşturulup kullanılabilmektedir. Her dil için string tanımlamaya örnek verelim.

<!--more-->
**Java:**
```java
String str = new String("Hasan Gok");
```
**C#:**
```csharp
string str = "Hasan Gok";
```
**C++:**
```cpp
char[10] str = "Hasan Gok\0";
string str = "Hasan Gok"; //(string.h kütüphanesi yardımı ile)
```
**String İşlemleri**

Bu üç dil için stringler üzerinde yapılan işlemlerden birkaç tanesine göz atalım. Tüm işlemlerde kullanmak için üç dil için de, içeriği farklı iki string değişkeni oluşturalım.

**Java:**
```java
String str1 = new String("Hasan");
String str2 = new String("Gok");
```
**C#:**
```csharp
string str1 = "Hasan";
string str2 = "Gok";
```
**C++:**
```cpp
char[30] str1 = "Hasan\0";
char[30] str2 = "Gok\0";
```
**Karşılaştırma:** Yukarıdaki gibi tanımlanmış str1 ve str2, birbirinden farklı stringler içeriyor olsun. Her dil için karşılaştırma ifadeleri aşağıdaki şekilde olur:

**Java:**
```java
if(str1 == str2) //bu şekilde iki stringin içeriği karşılaştırılır
	System.out.println("Stringler ayni");
else
	System.out.println("Stringler farkli");
```
Burada gördüğümüz gibi string türünden iki değişkeni, tıpkı tamsayılarda olduğu gibi karşılaştırmamız mümkün. Başta belirttiğimiz gibi stringler birbirlerinden farklı olduğundan bu kod parçası konsol ekranına "Stringler farkli" yazacaktır.

**C#:**

Java'da olduğu gibi bir if deyimi ile stringleri karşılaştırmaya C# dili de izin veriyor. Aynı örneği tekrarlamak yerine C#'ın String.Compare metoduna bir örnek verelim:
```csharp
if (String.Compare(str1, str2) == 0)	//eşit ise
if (String.Compare(str1, str2) == -1)	//ilk string büyük ise
if (String.Compare(str1, str2) == 1)	//ilk string küçük ise
```
Burada büyüklük küçüklük kavramı ilk karakterin ASCII kodunun diğerinden önce veya sonra olması anlamındadır.

**C++:**
```cpp
donus = strncmp (str1,str2,sayi);
```
Bu fonksiyon str1 içinde str2'nin "sayi" adet karakterini karşılaştırır. Fonksiyonunun dönüş değerleri, bize karşılaştırdığımız iki string arasındaki durumu verir. Dönüş değeri 0 ise iki string eşittir. str1, str2'den küçük olursa negatif bir tamsayı, büyük olursa pozitif bir tamsayı döner.

**Birleştirme:** Daha önceden tanımladığımız değişkenlerimizi birleştirmek için yapmamız gerekenlere de yine üç dil için de bakalım:

**Java:**

Java'da stringleri birleştirmek için "concat" metodu ve  + operatörü kullanılabilir. Aşağıda her iki satırdaki kod da str3'ün değerini "Hasan Gok" yapacaktır.
```java
String str3 = str1.concat(str2);
String str3 = str1 + str2;
```
**C#:**

Aynı şekilde + operatörü stringleri birleştirmek için kullanılır. str3'ün değeri "Hasan Gok" olacaktır.
```csharp
string  str3 = str1 + str2;
```
**C++:**

C++ dilinde karakter dizisi olarak tanımladığımız stringleri strncpy() fonksiyonu yardımı ile birleştirebiliriz. Üç parametre alan bu fonksiyon ilk parametresine hedef stringi, ikinci parametresine kaynak stringi alır ve üçüncü parametrede belirtilen sayı kadar karakteri kaynaktan hedef stringe kopyalar. Yukarıdaki dillere kıyasla zahmetli bir işlemdir.
```cpp
strncpy (str1,str2,4);	// \0 bitiş karakteri de dahil 4 karakter
```
Bu kod ile de str1 stringine str2'den 4 karakter kopyalanır. Programda bu satır çalıştıktan sonra str1'in değeri "Hasan Gok\0" olur.

**Stringlerin Uzunluğunu Bulma:** Tanımladığımız string değişkenlerinin sakladığı metnin kaç karakter içerdiğini kontrol etmek isteyebiliriz. Tanımlanan str1 ve str2 stringlerimizin kaç karakter içerdiklerini bulup, her üç dil için de karakterSayisi tamsayı değişkenine atayalım:

**Java:**
```java
int karakterSayisi1 = str1.lenght();	//1. Stringin uzunluğunu alır
int karakterSayisi2 = str2.lenght();	//2. Stringin uzunluğunu alır
```
**C#:**
```csharp
int karakterSayisi1 = str1.Length;	//1. Stringin uzunluğunu alır
int karakterSayisi2 = str2.Length;	//2. Stringin uzunluğunu alır
```
**C++:**
```cpp
int karakterSayisi1 = strlen(str1);	//1. Stringin uzunluğunu alır
```
strlen() fonksiyonunu dizimizdeki karakterleri tek tek sayarak uzunluğunu bulur. C++'da bu fonksiyon aşağıdaki gibi tanımlanmıştır:
```cpp
unsigned bizimStrLen(char * str)
{
	unsigned uzunluk;
	while (*str != "\0")
	{
		++uzunluk;
		++str;
	}
	return uzunluk;
}
```
**Alt String Arama:** Elimizdeki stringlerin birbirini içerip içermediğini kontrol etmemiz gerekebilir. str2'nin, str1 içinde yer alıp almadığını kontrol eden metod ve fonksiyonlara üç dil için de bakalım:

**Java:**

Java için alt string arama metodarından üç tanesine bakalım. Bu üç metod sırasıyla str1'in str2 ile başlayıp başlamadığını, str1 içinde herhangi bir yerde str2 olup olmadığını ve str1'in str2 ile bitip bitmediğini kontrol eder. Aşağıdaki örnekler için sonuç "True" ya da "False" olarak bir boolean değişkene yazılacaktır.
```java
boolean  b = str1.startsWith(str2);
boolean  b = str1.endsWith(str2);
b = str1.indexOf(str2) &gt; 0;
```
**C#:**

C# dili içinde de arama metodu bir boolean değer döndürür. Bizim örneğimiz için str1, str2'yi içermediği için b = False olacaktır. Kullanımı aşağıdaki gibidir.
```csharp
bool b = str1.Contains(str2);
```
**C++:**

Alt stringler strstr() fonksiyonu ile aranabilir. Stringlerimizi karakter dizisi olarak tanımladığımızdan, str1'in içinde str2 varsa; str2'nin, str1 içindeki kaçıncı karakterden başladığını gösteren bir karakter işaretçisi (pointer) döner. Bulunamazsa NULL değer dönecektir.
```cpp
char * baslangic = strstr (str1,str2);
```
**Çok Önemli Not:** Bu yazıyı programlama dilleri dersi ödevi için birkaç saatlik araştırma sonucunda yazdım. C++ ve Java hakkında hemen hemen hiçbir bilgim yoktur, o yüzden yazıda hatalar olması muhtemeldir. Lütfen görürdüğünüz hataları alta yorum yazarak gideriniz.
