---
layout: post
title: İlk C Programımız
date: 2009-04-03 22:07
author: hasangok
comments: true
categories: [C, C Programlama, ilk, program]
---
Her kitapta ilk program olarak ekrana "Merhaba Dünya" diye yazdırılır adettendir. Ben de adeti bozmayıp aynı programı anlatmaya çalışacağım sizlere. Mini programımızın kodları aşağıdaki gibi olacak. Bir göz aşinalığı olması açısından tamamını (noktası virgülü dahil) bir okuyun. Sonra da açıklamalarımıza devam edelim.
```c
#include<stdio.h>
int main(void)
{
	printf("Selamun aleykum");
	return 0;
}
```
İşte bu C ile yazdığımız ilk programımız olacak. Derleyip çalıştırdığınızda komut isteminde siyah bir ekran açılacak ve "Selamun aleykum" yazacak. (Derlemek de nedir? diye soranlar yazımın devamını sabırla okusun)

Şimdi bu programı satır satır inceleyip hangi kodun ne iş yaptığını açıklamaya çalışalım.

**#include<stdio.h>**: Burada Standart Input/Output header dosyasını programımıza eklemiş oluyoruz. Böylece bu başlık dosyasında tanımlanmış komutları kullanabileceğiz (printf bunlardan birisidir)

**int main(void)**: Bu kısım her programda yer almak zorundadır. Her C programında bir ana fonksiyon bulunmak zorundadır. O da burada gördüğümüz main fonksiyonunun ta kendisidir. En baştaki "int" ve parantez içindeki "void" ifadelerinin ne olduğuna şimdilik kafa yormayalım. İlerleyen yazılarımda onların da ne ie yaradıklarından bahsedeceğim. Şimdilik standart olarak böyle olduklarını varsayalım.

**main**’den sonra gelen **{** işareti ana fonksiyonun başladığını belirtir ve ana fonksiyonda çalışacak tüm komutlar başla ve bitir anlamlarını taşıyan "**{**" ve "**}**" işaretleri arasında yer alır.

**printf("Selamun aleykum");** printf ekrana birşeyler yazmak istediğimizde kullanacağımız komut. Burada gördüğümüz şekilde kullanılır ve noktalı virgül ile sona ermek zorundadır (sadece bu değil yazdığımız her komuttan sonra noktalı virgül kullanmak zorundayız). Ayrıca programlarımızın hiçbirinde Türkçe karakter kullanmayacağız bunu da burada söylemiş olayım.

**return 0;** Bu da ilerleyen derslerde üstünde duracağım bir konu. Şimdilik standart olarak her programda yer alan bir komut olarak varsayalım. Ama şunu söyleyeyim programımız hiçbir iş yapmadığı için return 0; komutunu hiçbirşeye (yani sıfıra) geri dönme olarak yorumlayabiliriz. (Ne, nereye, nasıl, niye döner ya da dönmek zorunda mıdır? İlerleyen yazılarımda)

Her satırdan yeteri kadar bahsettik sanırım. Programımıza yazdığımız kodların bilgisayar tarafından ne şekilde algılanacağını özetleyecek olursak: (sırasına göre)
1. Standart giriş çıkış başlık dosyasını kullanacağım haberin olsun
2. Ana fonksiyonum int tipinde olacak (takılmayın şimdilik)
3. Başladım ("**{**")
4. Ekrana "*Selamun aleykum*" yaz
5. Hiçbirşeye dönmene gerek yok
6. Ve bitirdim ("}")

İşte her satırda programımıza bunları yapmasını söyledik ve böylece anlaşıp istediğimizi yaptırdık.

Tamam ama bütün bunları nereye yazacağım ben ne şekilde çalıştıracağım? Tabi ki konunun en önemli kısımlarından birisi de bu. Piyasada bir sürü ücretsiz derleyici (compiler) var. Ben Dev-C++ adlı programı kullanmanızı öneriyorum. Hem küçük boyutlu, hem pratik, hem ücretsiz, hem zahmetsizce yazdıklarınızı çalıştırabiliyorsunuz. İndirip yüklemek için [buraya](http://prdownloads.sourceforge.net/dev-cpp/devcpp-4.9.9.2_setup.exe) tıklayabilirsiniz.

Dev-C++ programımızı çalıştırdıktan sonra Dosya &gt; Yeni &gt; Kaynak Dosyası (File &gt; New &gt; Source File) yolunu takip ederek kendimize kodlarımızı yazabileceğimiz, kalbimiz kadar temiz bir sayfa açıyoruz. Buraya yukarıdaki şekilde kodlarımızı yazıyoruz. Ve Çalıştır &gt; Derle &amp; Çalıştır (Execute &gt; Compile &amp; Run) yolunu izleyerek önce dosyamızı kaydediyor. Sonra derliyor, sonra da çalıştırıyoruz.

Bi çok arkadaş "İyi ama hemen kapanıyor hiçbirşey göremiyorum" diyecektir. Bunun sebebi hatalı kodlama yapmanız değildir. Windows’un dos uygulamalarına olan gıcığıdır :D Eğer programınızı daha sağlıklı görüntülemek istiyorsanız (yani daha göremeden kaybolmasın) Komut İstemi ile programınıza ulaşıp çalıştırabilirsiniz.

İlk programımızı böylece yazıp başarıyla çalıştırmış olduk. Çok güzel anlattığım için kendimi, çok güzel anladığın için de seni tebrik ediyorum ;)

Konuyla alakalı bir sonraki yazımda printf ve scanf komutları üzerinde duracağım. Değişken tanımlama, bu değişkenlere değer atama gibi basit şeyleri de aradan çıkaracağım.

Beni takip etmeye devam et.
Görüşmek dileğiyle...
