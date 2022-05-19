---
title: Windows 8 Yüklenememe Sorunu
date: 2013-08-03 01:15
---

![Windows-8-logo](/uploads/2013/08/Windows-8-Logo-small.png)

Daha önce yazmamıştım, *Asus*'un muhteşem bilgisayarlarından birisi olan ***N56VZ*** model bir bilgisayar kullanıyorum. Bu bilgisayarı aldığım gün yaptığım ilk iş, içinde yüklü gelen Windows 8'i silip zaten bir lisansa sahip olduğum Windows 7'yi yüklemek olmuştu. Günler, aylar geçti ve ben tekrar Windows 8 kullanmaya karar verdim. MSDN'den edindiğim Windows 8 iso dosyası ile kurulum yapmaya çalıştığımda ise şöyle bir hata ile karşılaştım:
*"Girilen ürün anahtarı yükleme işleminde kullanılabilecek hiçbir Windows görüntü dosyasıyla eşleşmiyor. Farklı bir ürün anahtarı girin."*

<!--more-->
![IMG_2147](/uploads/2013/08/IMG_2147.jpg)

Aslında bilgisayarı ilk aldığım zamanlar Windows 8 yüklü gelen bilgisayarların lisans anahtarlarının **BIOS**'a gömülü geldiğini ve tekrar yüklemeye çalışıldığında bu anahtarı otomatik okuduğu için size hiç lisans anahtarı sormadığını, dolayısıyla geçersiz ürün anahtarı hatası verip yüklemeye devam etmediğini duymuştum, ancak başıma gelmediği için nasıl bir çözümü olduğuyla ilgilenmedim.
Bugün bu sorunlar karşılaşınca küçük bir araştırma yaptım ve çözümünü buldum.

1. Yapmamız gereken ilk şey Windows'u DVD'den değil ***USB***'den kurmak. [Şu link](http://www.microsoftstore.com/store/msusa/html/pbPage.Help_Win7_usbdvd_dwnTool)ten edinebileceğiniz "**Windows 7 USB/DVD download tool**" ile Windows 8'in iso dosyasını kullanarak bir USB disk oluşturuyoruz.
2. Oluşturduğumuz USB diskin "***sources***" klasörü altında "***PID.txt***" adlı bir dosya oluşturuyoruz ve yükleme sırasında kullanacağımız lisans anahtarını aşağıdaki formatta bu dosyaya kaydediyoruz:

```
[PID]
Value=XXXXX-XXXXX-XXXXX-XXXXX-XXXXX
```

Kurulumu tekrar başlattığınızda BIOS'ta kayıtlı olan lisans anahtarı yerine, sizin PID.txt dosyasına kaydettiğiniz anahtar kullanılıyor. Bu sorun da böylece çözülmüş oluyor. Windows 8 ilk çıktığında 29 TL'ye sattığı bir çok lisans anahtarı bu tip hatalar yüzünden kullanılamadı, bunları her türlü forumda görmek mümkün. Microsoft, günümüzde her türlü hile ile aşılabilen bu tip küçük önlemler almasa keşke de bizler de uğraşmak zorunda kalmasak değil mi? 🙂

Neyse, sevgiler efendim,

Başka bir yazıda görüşmek dileğiyle...
