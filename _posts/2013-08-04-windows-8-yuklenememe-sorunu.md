---
layout: post
title: Windows 8 Yüklenememe Sorunu
date: 2013-08-04 01:15
author: hasangok
comments: true
Tags: [Asus N56VZ, Bilgisayar, PID.txt, Ürün Anahtarı Sorunu, Windows 8]
---
<p style="text-align: justify;"><img class="alignleft  wp-image-156" src="https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/08/Windows-8-Logo-small.png" alt="Windows-8-logo" width="123" height="123" />Daha önce yazmamıştım, <em>Asus</em>'un muhteşem bilgisayarlarından birisi olan <strong><em>N56VZ</em></strong> model bir bilgisayar kullanıyorum. Bu bilgisayarı aldığım gün yaptığım ilk iş, içinde yüklü gelen Windows 8'i silip zaten bir lisansa sahip olduğum Windows 7'yi yüklemek olmuştu. Günler, aylar geçti ve ben tekrar Windows 8 kullanmaya karar verdim. MSDN'den edindiğim Windows 8 iso dosyası ile kurulum yapmaya çalıştığımda ise şöyle bir hata ile karşılaştım:</p>
<p style="text-align: justify;"><em>"Girilen ürün anahtarı yükleme işleminde kullanılabilecek hiçbir Windows görüntü dosyasıyla eşleşmiyor. Farklı bir ürün anahtarı girin."</em></p>
<p style="text-align: justify;"><img class="aligncenter size-full wp-image-155" src="https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/08/IMG_2147.jpg" alt="IMG_2147" width="855" height="570" /></p>
<p style="text-align: justify;"><!--more--></p>
<p style="text-align: justify;">Aslında bilgisayarı ilk aldığım zamanlar Windows 8 yüklü gelen bilgisayarların lisans anahtarlarının <strong>BIOS</strong>'a gömülü geldiğini ve tekrar yüklemeye çalışıldığında bu anahtarı otomatik okuduğu için size hiç lisans anahtarı sormadığını, dolayısıyla geçersiz ürün anahtarı hatası verip yüklemeye devam etmediğini duymuştum, ancak başıma gelmediği için nasıl bir çözümü olduğuyla ilgilenmedim.</p>
<p style="text-align: justify;">Bugün bu sorunlar karşılaşınca küçük bir araştırma yaptım ve çözümünü buldum.</p>

<ol style="text-align: justify;">
	<li><span style="line-height: 14px;">Yapmamız gereken ilk şey Windows'u DVD'den değil <strong><em>USB</em></strong>'den kurmak. <a href="http://www.microsoftstore.com/store/msusa/html/pbPage.Help_Win7_usbdvd_dwnTool" target="_blank">Şu link</a>ten edinebileceğiniz "<strong>Windows 7 USB/DVD download tool</strong>" ile Windows 8'in iso dosyasını kullanarak bir USB disk oluşturuyoruz.
</span></li>
	<li>Oluşturduğumuz USB diskin "<em><strong>sources</strong></em>" klasörü altında "<em><strong>PID.txt</strong></em>" adlı bir dosya oluşturuyoruz ve yükleme sırasında kullanacağımız lisans anahtarını aşağıdaki formatta bu dosyaya kaydediyoruz:[PID]
Value=XXXXX-XXXXX-XXXXX-XXXXX-XXXXX</li>
</ol>
<p style="text-align: justify;"><span style="line-height: 18px;">Kurulumu tekrar başlattığınızda BIOS'ta kayıtlı olan lisans anahtarı yerine, sizin PID.txt dosyasına kaydettiğiniz anahtar kullanılıyor. Bu sorun da böylece çözülmüş oluyor. Windows 8 ilk çıktığında 29 TL'ye sattığı bir çok lisans anahtarı bu tip hatalar yüzünden kullanılamadı, bunları her türlü forumda görmek mümkün. Microsoft, günümüzde her türlü hile ile aşılabilen bu tip küçük önlemler almasa keşke de bizler de uğraşmak zorunda kalmasak değil mi? :)</span></p>
Neyse, sevgiler efendim,
Başka bir yazıda görüşmek dileğiyle...
