---
layout: post
title: Hyper-V'den VirtualBox'a Taşınmak
date: 2013-05-11 00:44
author: hasangok
comments: true
Tags: [Bilgisayar, hyper-v, vhdx, virtualbox]
---
Merhaba arkadaşlar,
İş yaşamım son sürat devam ederken *Windows 8*, *Hyper-V*, *Sharepoint*, *Visual Studio* gibi ürünlere her geçen gün biraz daha adapte olmaktayım. Bu adapte olma sürecinde karşılaştığım birkaç problemden birisi (ve en can sıkıcı olanı) *yavaşlık*! Sanal bilgisayarlarımızda çalışan *Windows Server 2008* ve *Sharepoint 2010* için ayırabildiğimiz **4 GB RAM** ve **i5** işlemcimizin bir çekirdeği ne yazık ki rahat bir çalışma ortamı için yeterli olamıyor. Yapılan iş didiklendikçe bu yavaşlık saç baş yolduran cinsten olabiliyor. Öyle ki tek satır kodda yapılan bir değişikliği debug edebilmek için 15 dakika beklemek insanı hem yoruyor hem şevkini kaçırıyor. Hele ki benim gibi işe yeni başlamış ve yapmaya çalıştığının çoğunu deneme yanılmayla çözmeye çalışan, binlerce kez değişiklik yapan ve sürekli debug modunda olan birisi için!

Her neyse, lafı daha fazla uzatmadan konuya gelecek olursak, kendimce çözümü kullandığımız çalışma ortamını şirketin verdiği bilgisayardan biraz daha güçlü olan kendi bilgisayarıma taşımakta ve çalışma ortamımızı barındıracak sanal bilgisayara **8 GB RAM** ve **i7** işlemcimin 2 çekirdeğini atamakta buldum. Ancak orda da sorun şuydu ki tüm alet edevatımız *Windows 8*’in sunduğu *Hyper-V* ile oluşturulmuş sanal bilgisayarlardaydı. Ben ise ısrarla *Windows 7* kullanmaya devam eden bir vatandaş olarak tüm bu ortamı *VirtualBox* ile çalıştırmak zorundaydım. Ve çalıştırdım. Şimdi sizlerle de bunu paylaşacağım ki Google’dan arayıp bu sayfalara kadar gelmişken eli boş dönmeyin :)
Öncelikle bilmemiz gereken (ve üzücü olan) şu ki VirtualBox ***VHDX*** biçimli sanal diskleri desteklemiyor. Benim bu yazıyı yazdığım sırada son sürüm olan 4.2.12 versiyonunda read-only (sadece okuma) desteği gelmiş olduğunu gördüm, ancak bu dosyayı kullanarak bir sanal makine oluşturmaya çalıştığımda başarılı olamadım. Bu yüzden öncelikle **Hyper-V Manager üzerinden hard diskimizi VirtualBox’ın da desteklediği VHD formatına çevirmemiz** gerekiyor. Bunun için aşağıdaki adımları takip ediyoruz:

1 .Hyper-V Manager açılır ve resimde gördüğünüz gibi ***New &gt; Hard Disk*** seçilir.
![1-hyper-v-new-hdd](https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/05/1-hyper-v-new-hdd.png)
2. Yeni diskimizi oluşturmak için sihirbaz bizi karşılar.
![2-new-hdd-wizard](https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/05/2-new-hdd-wizard.png)
3. “***Choose Disk Format***” aşamasında VirtualBox’ın kullanabileceği dosya biçimi olan **VHD** seçilir.
![3-choose-disk-format](https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/05/3-choose-disk-format.png)
4. Disk türü olarak ben kullanıldıkça büyüyen “***Dynamically Expanding***” seçeneğini kullandım. İhtiyacınıza göre size uygun seçenek seçilir.
![4-choose-disk-type](https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/05/4-choose-disk-type.png)
5. Hard diskimizin kopyalanacağı yeni dosyamız için bir isim ve yol belirtilir.
![5-name-and-location](https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/05/5-name-and-location.png)
6. Bu adımda üçüncü sırada olan “***Copy the contents of the specified virtual hard disk***” seçilir ve **VHDX** uzantılı dosyamız seçilir.
![6-configure-disk](https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/05/6-configure-disk.png)
7. Finish butonuna basılır ve diskin kopyalanması beklenir.
![7-summary-finish](https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/05/7-summary-finish.png)

**40 GB**’lık bir disk için bu işlemin tamamlanması hemen hemen bir saati buldu. Kaynak hard disk dosyanızın boyutu büyükse bu aşamada bir çay veya kahve molası vermek bilgisayar başında bekleyip sıkılmamanız için iyi bir seçenek olabilir :)
Buraya kadar olan kısımda *Hyper-V* ile olan işimizi bitirip, *VirtualBox*’a göç için hazırlanmış oluyoruz. Elimizde [buradan](http://download.virtualbox.org/virtualbox/4.2.12/VirtualBox-4.2.12-84980-Win.exe) ulaşabileceğimiz *VirtualBox* ve az önce hazırladığımız ***VHD*** uzantılı hard disk var. Geriye bu hard diski kullanacak bir sanal bilgisayar oluşturmak kalıyor. Bunun için aşağıdaki adımları takip edebilirsiniz:

1. VirtualBox açılır, **New** butonuna basarak sihirbaz başlatılır.
2. Bilgisayar için bir isim verilir ve işletim sistemi seçilir.
3. Bilgisayar için ayrılacak RAM seçilir.
4. Hard disk için “**Use an existing virtual hard drive file**” seçeneği kullanılarak Hyper-V ile oluşturduğumuz VHD uzantılı dosya seçilir.
5. **Create** butonuna basarak sihirbaz sonlandırılır.
6. Settings kısmından istenilen diğer ayarlar (ekran kartı belleği, işlemci çekirdek sayısı gibi) yapılır.

Buraya kadar her şey sorunsuz ve *Hyper-V*’deki çalışma ortamımız olduğu gibi *VirtualBox*’ta! Harika! Hemen sanal bilgisayarımızı çalıştırıyoruz ve aşağıdaki görüntüyle karşılaşıyoruz.
![8-mavi-ekran-hata](https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/05/8-mavi-ekran-hata.png)

Mavi ekran! En sevdiğimiz. Zaten çoktandır görmüyorduk, özlemişiz :)
Aldığımız bu güzel **mavi ekran hatasının sebebi** şuymuş: *Hyper-V, sadece bootable IDE hard diskler oluşturuyormuş. Ancak Settings &gt; Storage bölümünden görebileceğiniz üzere VirtualBox bu hard diski SATA Controller altında çalıştırmaya çalışıyor. Bu yüzden Settings &gt; Storage yolunu takip edip SATA Controller’ı tamamen silmeli ve hard disk dosyanızı IDE Controller altına tekrar eklemelisiniz.* Bu son değişiklik ile tüm sorunlarınız halledilmiş oluyor ve sanal bilgisayarımız sorunsuz çalışıyor.
Eveeeet. Bu yazıyı burada bitirelim. Zaten attığım başlığa ek bir sürü hikaye de anlatmış oldum, ama siz adımları ve resimleri takip ederek zaten hikaye kısmını atlamışsınızdır diye tahmin ediyorum :)
Haydi başka bir yazıda görüşürüz efendim, sağlıcakla kalın...
