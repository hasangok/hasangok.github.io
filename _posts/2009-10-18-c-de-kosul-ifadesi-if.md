---
title: C'de Koşul İfadesi - if
date: 2009-10-18 22:22
---

Değişken tanımlamayı, türlerini, printf ve scanf fonksiyonlarını öğrendikten sonra programlarımıza biraz daha işlev katacak olan seçme komutlarından ve döngülerden bahsedebiliriz.

"if" C dilindeki seçme komutudur. Türkçesi "eğer" olan bu komut, verdiğiniz şarta göre programınızın ne yapacağını belirler. Şart doğruysa yazdığınız işlemleri yapar, değilse bakmadan geçer. Nasıl kullanıldığını ve tam olarak ne işe yaradığını bir örnekle görelim:

<!--more-->
Kullanıcıdan 3 tamsayı alıp, bunlardan en büyüğünü ekrana yazdıran örnek programımıza bir göz atalım.
```c
#include &lt;stdio.h&gt;
int main(void)
{
	int sayi1,sayi2,sayi3,enbuyuk;
	scanf("%d%d%d",&sayi1,&sayi2,&sayi3);
	enbuyuk=sayi1;
	if(sayi2>enbuyuk) enbuyuk=sayi2;
	if(sayi3>enbuyuk) enbuyuk=sayi3;
	printf("Girilen en buyuk sayi: %d",enbuyuk);
	return 0;
}
```
Şimdi zaten biliyor olduğumuz tanımlama satırlarını atlayıp programcığımızın büyük sayıyı ne şekilde bulduğunu inceleyelim:

Kullanıcıdan aldığımız 3 adet sayının ilkini, yani sayi1 adlı değişkenin en büyük olduğunu varsaydık ve "enbuyuk" adını verdiğimiz değişkene bu değeri verdik. if(sayi2&gt;enbuyuk) diyerek, en büyük olduğunu varsaydığımız sayıyı sayi2 ile karşılaştırdık. Eğer sayi2 daha büyükse "enbuyuk" adlı değişken sayi2’nin değerini alacak, değilse diğer satıra geçecek. Bir sonraki adımda yine aynı işlem tekrarlanacak. Bu kez sayi3’ün mü yoksa "enbuyuk" adlı değişkenin mi büyük olduğu kontrol edilecek. Hangisi daha büyükse "enbuyuk" adlı değişken o değeri alacak ve en sondaki "printf" ile kullanıcıya gösterilecek. İşte bu kadar basit...

"if" komutunun nasıl kullanıldığını anladığımıza göre "çift yönlü if" dediğimiz "if-else" yapısına bakabiliriz. Karşılaştırma mantığı birebir aynı olsa da, if-else ile şart sağlanmadığında programımızın ne yapması gerektiğini de belirtebiliyoruz. Yeni bir örnek yapmaktansa sadece bu kullanımı örnekleyen bir program parçasına göz atalım:
```c
printf("Sartimiz saglanirsa toplami 1 arttiralim");
printf("Eger saglanmiyorsa da toplami 1 azaltalim");
if(sart&gt;0) toplam=toplam+1;
else toplam=toplam-1;
```
Program parçacığında printf ile de yazdırıldığı gibi, eğer "sart" adlı değişken sıfırdan büyükse "toplam" değişkeni 1 arttırılıyor, değilse (else) bir azaltılıyor. 1 arttırma ya da azaltma işlemleri "toplam++;" ve  "toplam--;" şeklinde de yapılabiliyor bu pratik değer atama yöntemini de burada belirtmiş olayım.

if ya da else ile kontrol ettikten sonra programımızın birden fazla işlem yapması gerekiyorsa köşeli parantezler ile kod bloğu oluşturuyoruz. Şöyle ki:
```c
if(sart&gt;0)
{
	toplam++;
	sayi1= yenideger;
	.
	.
	.
}
```
Bu yazı ile "if-else" komutlarını da kısaca tanımış olduk. Bir sonraki yazıda yine seçme komutlarından birisi olan "switch" komutundan bahsedeceğim. Böylece sonunda döngü (loop) komutlarına geçebileceğiz 🙂
