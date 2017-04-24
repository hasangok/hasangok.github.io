---
layout: post
title: SSD Disk Alanı Optimizasyonu
date: 2013-08-07 14:13
author: hasangok
comments: true
Tags: [Bilgisayar, hiberfil.sys, pagefile.sys, SSD Optimizasyonu]
---
<p style="text-align: justify;">SSD kullanıcılarının en büyük sorunlarından birisi disk alanının çabuk tükenmesi olsa gerek. Fiyatları yüzünden büyük boyutlu diskler alamadığımızdan elimizdeki küçük diskleri optimum şekilde kullanmanın bir yolunu bulmamız gerekiyor. Kullandığım 120 GB SSD'nin 20 GB'lık kısmını boş yere kullanan Windows 8'de, sadece aşağıdaki 3 ayarları yaparak 20 GB kadar kar ettim.</p>
<p style="text-align: justify;"><strong>1. Sistem Koruması'nı kapatmak</strong></p>
<p style="text-align: justify;">Millennium Edition çıktığından bu yana Windows kullanırım, daha bir kez bu özelliğinden faydalanmadım. Sizin de kullanmadığınızı ve kullanmayacağınızı varsayarak <em>Sistem Koruması</em>'nı kapatmanızı öneririm. Bilgisayar özelliklerinden Sistem korumasına tıklayıp, buradan tamamen kapatabilirsiniz.</p>
<p style="text-align: justify;"><!--more--></p>
<p style="text-align: justify;"><img class="aligncenter size-full wp-image-161" src="http://www.hasangok.com.tr/wp-content/uploads/2013/08/sistem-korumasi.png" alt="sistem-korumasi" width="491" height="581" /></p>
<p style="text-align: justify;"><strong>2. hiberfil.sys dosyasını kaldırmak</strong></p>
<p style="text-align: justify;">Windows'u kurduğumuz dizinde bulunan bu dosya, genellikle RAM ile aynı boyuttadır ve bilgisayarımızı uyku moduna aldığımızda RAM'deki bilgilerin diskte saklanmasını sağlar. <em>Uyku Modu</em>'nu kullanmayıp, disk alanından 16 GB kar etmek benim için mantıklı bir seçenek oldu. Siz de <em>Uyku Modu</em>'ndan vazgeçip RAM miktarınız kadar alandan tasarruf etmek isterseniz bir komut penceresini yönetici olarak açıp, aşağıdaki komutu çalıştırabilirsiniz:</p>
<p style="text-align: justify;"><img class="aligncenter size-full wp-image-165" src="http://www.hasangok.com.tr/wp-content/uploads/2013/08/powercfg-h-off.png" alt="powercfg-h-off" width="643" height="272" /></p>
<p style="text-align: justify;"><strong>3. pagefile.sys dosyasını kaldırmak</strong></p>
<p style="text-align: justify;">Bu dosya sanal bellek dosyasıdır ve RAM'in yetersiz kaldığı durumlarda diski kullanmak için kullanılır. Eğer sisteminizde yeterli RAM varsa ve tamamını hiçbir zaman kullanmıyorsanız sanal bellek kullanımından da vazgeçebilirsiniz.</p>
<p style="text-align: justify;">Bunu yapmak için şu yolu takip ediyoruz: <em>Bilgisayar özellikleri</em> &gt; <em>Gelişmiş sistem ayarları</em> &gt; <em>Performans</em> &gt; <em>Ayarlar</em> &gt; <em>Gelişmiş</em> &gt; <em>Sanal Bellek</em> &gt; <em>Değiştir</em></p>
<p style="text-align: justify;">Burada "<em>Tüm sürücülerde disk belleği dosyası boyutunu otomatik yönet</em>" seçeneğini kaldırıyor ve "<em>Disk belleği dosyası yok</em>" seçiyoruz. Bilgisayarımız yeniden başladığında <em><strong>pagefile.sys</strong></em> dosyası da artık var olmayacak.</p>
<p style="text-align: justify;"><img class="aligncenter size-full wp-image-162" src="http://www.hasangok.com.tr/wp-content/uploads/2013/08/sanal-bellek.png" alt="sanal-bellek" width="501" height="573" /></p>
<p style="text-align: justify;">Benim için sonuç aşağıdaki gibi oldu. Diskte 19,4 GB alan açıldı.</p>
<p style="text-align: justify;"><a href="http://www.hasangok.com.tr/wp-content/uploads/2013/08/disk-alani-karsilastirma.png"><img class="aligncenter size-full wp-image-163" src="http://www.hasangok.com.tr/wp-content/uploads/2013/08/disk-alani-karsilastirma.png" alt="disk-alani-karsilastirma" width="992" height="596" /></a>Bu ayarların hepsinin Windows 7 için de kullanılabileceğini belirtmek istiyorum. Artık açtığım alana MATLAB yükleyebilirim :)</p>
<p style="text-align: justify;">Görüşmek dileğiyle efendim,
Sağlıcakla kalın.</p>
<p style="text-align: justify;"></p>
