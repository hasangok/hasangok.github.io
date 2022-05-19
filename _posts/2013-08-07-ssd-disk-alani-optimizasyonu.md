---
title: SSD Disk Alanı Optimizasyonu
date: 2013-08-07 14:13
---

SSD kullanıcılarının en büyük sorunlarından birisi disk alanının çabuk tükenmesi olsa gerek. Fiyatları yüzünden büyük boyutlu diskler alamadığımızdan elimizdeki küçük diskleri optimum şekilde kullanmanın bir yolunu bulmamız gerekiyor. Kullandığım 120 GB SSD'nin 20 GB'lık kısmını boş yere kullanan Windows 8'de, sadece aşağıdaki 3 ayarları yaparak 20 GB kadar kar ettim.

<!--more-->
**1. Sistem Koruması'nı kapatmak**
Millennium Edition çıktığından bu yana Windows kullanırım, daha bir kez bu özelliğinden faydalanmadım. Sizin de kullanmadığınızı ve kullanmayacağınızı varsayarak *Sistem Koruması*'nı kapatmanızı öneririm. Bilgisayar özelliklerinden Sistem korumasına tıklayıp, buradan tamamen kapatabilirsiniz.

![sistem-korumasi](/uploads/2013/08/sistem-korumasi.png)

**2. hiberfil.sys dosyasını kaldırmak**
Windows'u kurduğumuz dizinde bulunan bu dosya, genellikle RAM ile aynı boyuttadır ve bilgisayarımızı uyku moduna aldığımızda RAM'deki bilgilerin diskte saklanmasını sağlar. *Uyku Modu*'nu kullanmayıp, disk alanından 16 GB kar etmek benim için mantıklı bir seçenek oldu. Siz de *Uyku Modu*'ndan vazgeçip RAM miktarınız kadar alandan tasarruf etmek isterseniz bir komut penceresini yönetici olarak açıp, aşağıdaki komutu çalıştırabilirsiniz:

![powercfg-h-off](/uploads/2013/08/powercfg-h-off.png)

**3. pagefile.sys dosyasını kaldırmak**
Bu dosya sanal bellek dosyasıdır ve RAM'in yetersiz kaldığı durumlarda diski kullanmak için kullanılır. Eğer sisteminizde yeterli RAM varsa ve tamamını hiçbir zaman kullanmıyorsanız sanal bellek kullanımından da vazgeçebilirsiniz.
Bunu yapmak için şu yolu takip ediyoruz: *Bilgisayar özellikleri* &gt; *Gelişmiş sistem ayarları* &gt; *Performans* &gt; *Ayarlar* &gt; *Gelişmiş* &gt; *Sanal Bellek* &gt; *Değiştir*
Burada "*Tüm sürücülerde disk belleği dosyası boyutunu otomatik yönet*" seçeneğini kaldırıyor ve "*Disk belleği dosyası yok*" seçiyoruz. Bilgisayarımız yeniden başladığında ***pagefile.sys*** dosyası da artık var olmayacak.

![sanal-bellek](/uploads/2013/08/sanal-bellek.png)

Benim için sonuç aşağıdaki gibi oldu. Diskte 19,4 GB alan açıldı.

![disk-alani-karsilastirma](/uploads/2013/08/disk-alani-karsilastirma.png)

Bu ayarların hepsinin Windows 7 için de kullanılabileceğini belirtmek istiyorum. Artık açtığım alana MATLAB yükleyebilirim 🙂
Görüşmek dileğiyle efendim,
Sağlıcakla kalın.
