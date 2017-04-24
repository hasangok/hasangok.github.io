---
layout: post
title: InfoPath Formlarından Ekran İpucunu (Tooltip) Kaldırma
date: 2013-12-06 21:59
author: hasangok
comments: true
Tags: [Ekran İpucu, InfoPath, Programlar, Sharepoint, SharePoint, Tooltip]
---
<p style="text-align: justify;"><img class="alignleft  wp-image-517" alt="infopath-logo" src="http://www.hasangok.com.tr/wp-content/uploads/2013/12/infopath-logo-150x150.png" width="108" height="108" />Efendim gün geçmiyor ki müşterilerimizden yeni bir istek gelmesin :) <em>Microsoft InfoPath</em> ile özelleştirdiğim bir <em>SharePoint</em> formu için, formu doldururken rahatsızlık verdiği gerekçesiyle, ekran ip ucunun (<em>tooltip</em>) kaldırılması istendi. Bu alanların zorunlu olmaları yerine, çeşitli kurallar yardımıyla boş geçilememesini sağlayacakken aşağıdaki gibi iki çözüm çıkageldi.</p>
<p style="text-align: justify;">İlki tavsiye edilen bir çözüm yöntemi değil. Çünkü hem dokunmamamız gereken "<em>14\TEMPLATE\LAYOUTS\INC</em>" klasörü içindeki "<strong>ifsmain.css</strong>" dosyasını düzenlememiz ve "<strong>.errorDiv</strong>" sınıfını bulup aşağıdaki değişikliği yapmamız gerekiyor. Bu değişiklik ihtiyacımızı görecek olsa da bundan sonra <em>InfoPath</em> ile oluşturacağımız tüm formları etkileyecek bir duruma sebep oluyor, ki bizim isteğimiz sadece ilgili formumuzda bu değişikliği gerçekleştirmek.</p>
<p style="text-align: justify;"><!--more--></p>
<p style="text-align: justify;">Tam burada ikinci yöntem devreye giriyor. Aşağıda gördüğünüz şekilde, tasarladığımız <em>InfoPath</em> formunda <em>Publish</em> menüsünden "<strong>Export Source Files</strong>" diyor ve dosyalarımızı bir klasör içerisine kaydediyoruz.</p>
<p style="text-align: justify;"><img class="aligncenter size-full wp-image-516" alt="infopath-publish" src="http://www.hasangok.com.tr/wp-content/uploads/2013/12/infopath-publish.png" width="734" height="781" /></p>
<p style="text-align: justify;">Daha sonra dosyalarımız içerisinden "<strong>view.xsl</strong>" adlı dosyayı bulup bir metin editörüyle düzenliyor ve "<strong>&lt;/body&gt;</strong>" etiketinin hemen üzerine aşağıdaki <em>CSS</em> kodlarını ekliyoruz:</p>

<pre class="lang:default decode:true">&lt;style title="myCustomStyleSheet" type="text/css"&gt;
	.errorDiv{display:none !important;}
&lt;/style&gt;</pre>
Bu değişikliği yapıp dosyayı kaydettikten sonra "<strong>manifest.xsf</strong>" dosyasına sağ tıklayıp <em>Tasarla</em> (<em>Design</em>) diyor ve formumuzu yayımlıyoruz (<em>publish</em>). Artık bu ekran ipuçları (<em>uyarı</em>, <em>tooltip</em>) müşterimizin canını sıkamayacak ;)

Kolay gelsin.
