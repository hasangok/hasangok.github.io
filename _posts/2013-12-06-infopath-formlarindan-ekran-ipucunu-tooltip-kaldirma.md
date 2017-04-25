---
layout: post
title: InfoPath Formlarından Ekran İpucunu (Tooltip) Kaldırma
date: 2013-12-06 21:59
author: hasangok
comments: true
Tags: [Ekran İpucu, InfoPath, Programlar, Sharepoint, SharePoint, Tooltip]
---
![infopath-logo](https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/12/infopath-logo-150x150.png)
Efendim gün geçmiyor ki müşterilerimizden yeni bir istek gelmesin :) *Microsoft InfoPath* ile özelleştirdiğim bir *SharePoint* formu için, formu doldururken rahatsızlık verdiği gerekçesiyle, ekran ip ucunun (*tooltip*) kaldırılması istendi. Bu alanların zorunlu olmaları yerine, çeşitli kurallar yardımıyla boş geçilememesini sağlayacakken aşağıdaki gibi iki çözüm çıkageldi.
İlki tavsiye edilen bir çözüm yöntemi değil. Çünkü hem dokunmamamız gereken "*14\TEMPLATE\LAYOUTS\INC*" klasörü içindeki "**ifsmain.css**" dosyasını düzenlememiz ve "**.errorDiv**" sınıfını bulup aşağıdaki değişikliği yapmamız gerekiyor. Bu değişiklik ihtiyacımızı görecek olsa da bundan sonra *InfoPath* ile oluşturacağımız tüm formları etkileyecek bir duruma sebep oluyor, ki bizim isteğimiz sadece ilgili formumuzda bu değişikliği gerçekleştirmek.

Tam burada ikinci yöntem devreye giriyor. Aşağıda gördüğünüz şekilde, tasarladığımız *InfoPath* formunda *Publish* menüsünden "**Export Source Files**" diyor ve dosyalarımızı bir klasör içerisine kaydediyoruz.
![infopath-publish](https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/12/infopath-publish.png)
Daha sonra dosyalarımız içerisinden "**view.xsl**" adlı dosyayı bulup bir metin editörüyle düzenliyor ve "**&lt;/body&gt;**" etiketinin hemen üzerine aşağıdaki *CSS* kodlarını ekliyoruz:

```html
&lt;style title="myCustomStyleSheet" type="text/css"&gt;
	.errorDiv{display:none !important;}
&lt;/style&gt;
```
Bu değişikliği yapıp dosyayı kaydettikten sonra "**manifest.xsf**" dosyasına sağ tıklayıp *Tasarla* (*Design*) diyor ve formumuzu yayımlıyoruz (*publish*). Artık bu ekran ipuçları (*uyarı*, *tooltip*) müşterimizin canını sıkamayacak ;)

Kolay gelsin.
