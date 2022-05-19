---
title: Değişken Tanımlama ve printf Fonksiyonu
date: 2009-04-15 22:33
---

Evet arkadaşlar artık ekrana "Selamun aleykum" yazabildiğimize göre, C dilinde bir adım daha ilerleyip *değişken tanımlama*, bu değişkenleri ekranda yazdırma gibi basit işlemlere de göz atabiliriz.

<!--more-->
Değişken tanımlamaya geçmeden önce bu değişkenlerin ne iş yaptığını bilmekte fayda var. Bilgisayarımızda yaptığımız işlemleri düşünelim (ki her türlü programın özünde yine bu işlemler vardır derslerde ilerledikçe anlayacaksınız) toplama, çıkarma, iki değeri karşılaştırma vs. gibi. Bu işlemleri yapmak için kullandığımız bilgileri değişkenler içinde saklarız. Kullanacağımız değişkeni çağırır işlemi yapar sonra gerekiyorsa yeni değerlerini söyler geri göndeririz. Kullanımını az sonraki program örneklerimizde de göreceğiz zaten o yüzden şimdi tanımlayacağımız değişkenlerin sahip olması gereken özelliklere göz atalım.

1. Tanımladığımız değişkenin adını amacına uygun seçmeliyiz (daha sonra kodları anlamak açısından yararlı olacak)
2. Değişkenlerimiz a-z ya da A-Z arasından bir karakterle başlamalıdır. Sayıyla başlayamayız. (Doğal olarak Türkçe karakterleri hariç tutuyoruz)
3. C dili büyük küçük harflere duyarlı bir dildir. Yani tanımladığınız Hasan, HAsan, HaSaN, HASAN gibi değişkenlerin her biri ayrı ayrı değişkenler olarak algılanır.
4. Değişken adında iki kelime kullanacağınız zaman arada boşluk bırakamazsınız. "vize notu" diye bir değişken olamaz. Vize_notu ya da VizeNotu gibi bir şey tercih etmeniz gerekir.
5. Değişkenleriniz içinde !, ?, {, ] gibi karakterler de kullanamazsınız.
6. Ve tabi ki C dilinde önceden tanımlı komut isimlerini de değişken adı olarak kullanamazsınız. Yani printf gibi, char gibi bir değişken adı olamaz.

Buradan kısaca şunu çıkaralım: Efendi olup doğru düzgün, adam akıllı değişken isimleri tanımlamamız gerekiyor 🙂 Ufak bir not da *NOT* kelimesine düşelim. "*not*" diye bir değişken de tanımlamamız gerekiyor olumsuz durumlarda kullanılan bir komut olduğu için.

Şimdi değişken tanımlamaya ve bu değişkenlerle işlem yapmaya örnek olacak basit bir program yazalım ve satır satır inceleyelim.
```c
#include<stdio.h>
int main(void)
{
	int sayi1=10, sayi2=20, toplam;
	toplam=sayi1+sayi2
	printf("%d", toplam);
	return 0;
}
```
Bir önceki yazımda açıklamasını yaptığım kısımları atlıyorum. Doğal olarak dördüncü satırdan başlıyorum. "***int sayi1=10, sayi2=20, toplam;***" yazıp acaba ne demeye çalıştık.

En başa yazdığımız "***int***" İngilizce *integer*’ın kısaltılmış oluyor. Yani tamsayı türünden değişken oluşturacağım demiş oluyoruz programımıza. Ben tek satırda aynı tipteki tüm değişkenlerin tanımlanmasından yanayım ama her değişkeni ayrı satırda tanımlamanız da mümkün. Tıpkı aşağıdaki gibi:
```c
int sayi1;
int sayi2;
int toplam;
sayi1=10;
sayi2=20;
```
Dikkat etmemiz gereken C dilinin gramerinin dışına çıkmamış olmak. Her satırdan sonra noktalı virgülümüzü koymayı unutmuyoruz. İkinci olarak verdiğim kodlara bakacak olursak önce değişkenleri tanımlayıp daha sonra bu değişkenlerimize tamsayı değerler atamışız. Değişkene değer atamak için "**DegiskenAdi=değer**" şeklinde yazmamız gerekiyor. "**değer=DegiskenAdi**" şeklinde bir atama mümkün değildir. Eşittirin soluna değişken adınızı yazmak zorundasınız. Neyse, bundan da kısaca bahsettik iki şekilde de değişken tanımlayıp değer atamak mümkün. Ben birinci şekilde kullanacağım anlatırken. Tek satırda tüm değişkenleri tanımlarken, ayrı değişkenlerimizi virgülle ayırıyoruz, en sonunda noktalı virgülle bitiriyoruz tekrar hatırlatmış olayım. Şimdi tekrar programımıza dönelim ve **printf("%d",toplam)****;** satırını açıklamaya devam edelim.

Daha önce Selamun Aleykum yazarken tırnaklar içine metin yazmıştık. ***%d*** ile tanımladığımız *tamsayı* tipi değişkenleri yazdırabiliyoruz. (veri tiplerine daha sonra ayrıntılı döneceğiz şimdilik sadece int tipli sayılarla uğraşalım) Aynı satırı "***printf("Toplam sayi %d",toplam);***" şeklinde de yazabilirdik tabi tırnak içini istediğimiz gibi kullanabiliyoruz hala. Aslında satırın anlamı basit: Programınız "*%d ile ekrana tamsayı yazmamı istemişler, tırnaktan ve virgülden sonraki değişken neyse onun değerini getirip %d gördüğüm yere yazayım en iyisi*" şeklinde düşünüyor ve düşündüklerini uyguluyor 🙂 Ve siz ekranınızda "***Toplam sayi 30***" görüyorsunuz. (Göremiyorum kapanıyor hemen diyenler bir önceki yazıma bakabilirler)

Değişkenin ne olduğunu, değişken tanımlamayı ve printf fonksiyonunda bu değişkenlerin kullanımının ne şekilde olduğunu gördükten sonra bir adım daha ilerlemiş oluyoruz. İlgili bir sonraki yazımda scanf fonksiyonu ile değişkenlerimize klavyemizden değer atamayı öğreneceğiz ve bunları yine çeşitli işlemlerde kullanıp ekrana yazdıracağız.

Tekrar yazıncaya dek kendinize iyi bakın efendim.
Esen kalın...
