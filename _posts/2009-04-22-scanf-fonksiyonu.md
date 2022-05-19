---
title: Scanf Fonksiyonu
date: 2009-04-22 21:52
---

Konuyla ilgili son yazımda değişken tanımlama ve printf fonksiyonu üzerinde durmuştuk. Hatırlarsanız herhangi bir değişkene atadığımız değeri ekranda yazdırabilmiştik. Şimdi bu işi bir adım daha ileriye götürelim ve değişkenlerimize klavyemizden değer girişini sağlayalım. x=100; diye baştan tanımlayacağımıza, programımızın kullanıcısı istediği değeri değiskenimize değer olarak atayabilsin.

<!--more-->
Bunu yapmak elbette mümkün ve yardımımıza koşan fonksiyonun adı "scanf". Scanf fonksiyonu ile tanımladığımız değişkenlere değer atayabileceğiz. Yine örnek olarak basit bir programcık yazıp, satır satır ne iş yaptığına göz atalım. Programımızın kodları şöyle olsun:
```c
#include&lt;stdio.h&gt;
int main(void)
{
	int sayi;
	printf("Lutfen degiskene atamak istediginiz degeri giriniz: ");
	scanf("%d", &amp;sayi);
	printf("\nDegiskene atadiginiz deger: %d", sayi);
	return 0;
}
```
İşte tanımladığımız "sayi" değişkenine scanf fonksiyonu ile klavyemizden değer okuduğumuz mini program. Şimdi bize yabancı tek satır olan 6. Satırın ne iş yaptığına bakalım.

Biliyoruz ki (en azından konumuz bu olduğundan tahmin ediyoruz) scanf ile değişkenlerimize klavyemizden değer giriyoruz. Tıpkı printf fonksiyonunda olduğu gibi yine veri tiplerimizi uygun seçmemiz gerekiyor. (Veri tiplerini daha sonra açıklayacağımı söylemiştim önceki yazılarda, şimdilik tamsayı tipindekilerle devam edelim) Değişkenimizi 4. satırda tamsayı tipinde tanımladık. Ve biliyoruz ki tamsayıları printf’te yazdırmak için kullandığımız ifade "%d" idi. O halde scanf fonksiyonumuzda da ne türden bir değer alacağımızı %d ile belirtiyoruz. Ve printf’tekinden farklı olarak virgülden sonra değişkenimizin önüne "&amp;" işaretini koyuyoruz. "Koymazsak ne olur?" diye merak eden arkadaş varsa deneyip görebilir: Çalışmaz 🙂 O işaret scanf’in olmazsa olmazıdır.

Scanf’in iş yaptığı satır bittiğine göre programımızın ne yapacağına göz atmaya devam edebiliriz. Değişkenimiz yeni değerini aldığına göre bir sonraki satırda girdiğimiz değeri ekrana yazdırabilecek. Klavyeden girdiğimiz tamsayı değerini printf ile ekranda gösterince programımız işini tamamlamış oluyor ve return 0; satırı ile de sona eriyor.

Bir dersimizin daha sonuna gelmiş bulunuyoruz. Bu dersimizle beraber C’de değişken tanımlama, değişkenlere değer atama, bu değişkenleri ekrana yazdırma ve tanımladığımız değişkenlere klavyemizden değer girişi gibi en temel unsurları öğrenmiş olduk. Bir sonraki yazımda veri tiplerinden bahsedeceğim. Böylece değişkenlere sadece tamsayı değerleri atamaktan da kurtulmuş olacağız 😉 Klavyemizden ondalıklı sayılar okuyup, hangisinin nerede ve ne şekilde kullanıldığına bir göz atıp biraz da o şekilde vakit geçiririz 🙂 Sonrası Allah kerim...

Diğer yazılarımda görüşünceye dek, esen kalın...
