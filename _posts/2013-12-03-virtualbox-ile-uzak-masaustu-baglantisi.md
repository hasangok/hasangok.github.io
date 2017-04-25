---
layout: post
title: VirtualBox ile Uzak Masaüstü Bağlantısı
date: 2013-12-03 23:52
author: hasangok
comments: true
Tags: [Programlar, Uzak Masaüstü Bağlantısı, virtualbox, VirtualBox Bridged Networking Driver]
---
![oracle-virtualbox](https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/12/oracle-virtualbox.png)
Kişisel bilgisayarımda çalışma ortamlarım (*Windows Server* ve *SharePoint*) *VirtualBox* üzerinde bulunuyor. Çalıştığım sunucuya zaman zaman başka kullanıcılar ile de bağlanıp bazı denemeler / kontroller yapmam gerekebiliyor. Her seferinde o anki kullanıcının oturumunu kapatıp, diğer kullanıcıya geçip, bir şeyler yapıp / deneyip tekrar diğer kullanıcıya geçmek nasıl bir işkence tahmin edebiliyorsunuzdur. Üşenmekten vazgeçtiğim zaman, başka bir kullanıcı ile *uzak masaüstü bağlantısı* yapmaya en çok ihtiyaç duyduğum "*SharePoint-Hosted Apps*" konulu bir yazı yazacağım, o zaman bu ihtiyacın nereden geldiğini daha iyi anlayacaksınız. Uzatmayayım, *VirtualBox* ile çalıştırdığımız bilgisayara *uzak masaüstü bağlantısı* (*RDP*) yapmamız gerekebiliyor. Bunun için herşeyden önce *VirtualBox* için *Extension Pack* indirip yüklememiz gerekiyor. Bu paketin sisteminizde kurulu olan *VirtualBox* ile aynı sürüm olması gerektiğini önemle vurgulayayım.

*Extension Pack* yüklendikten sonra yapmamız gereken ilk iş, uzak masaüstü bağlantısı yapacağımız bilgisayarın özelliklerinden **Uzak bağlantı ayarları** (*Remote settings*) diyalogunu açıp aşağıda gördüğünüz gibi bu özelliği aktif hale getirip bağlanabilecek kullanıcıları seçmek.
![windows-server-enable-remote-desktop](https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/12/windows-server-enable-remote-desktop.png)
Daha sonra *VirtualBox*'tan ilgili bilgisayarı seçip **Settings**'e tıklayarak *Display* altındaki *Remote Display* sekmesinden "**Enable Server**" özelliğini aktif hale getirmemiz gerekiyor.
![virtualbox-enable-remote-display](https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/12/virtualbox-enable-remote-display.png)
Yine aynı yerden *Network* altında herhangi bir ağ adaptörünü aktif hale getirerek "**Attach to: Bridged Adapter**" seçiyor ve internete bağlantığımız ağ bağdaştırıcısını seçiyoruz.
![virtualbox-network-bridged-adapter](https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/12/virtualbox-network-bridged-adapter.png)
**Önemli Not:** "*Bridged Adapter*" seçemiyorsanız, yani bu alan boş geliyorsa, *VitrualBox*'ı kurarken yönetici yetkileriyle kurmamışsınız, dolayısıyla kurulum sırasında mevcut ağınıza ilgili özellikler eklenememiş demektir. Bunu elle yapmamız gerekiyor.
*Ağ ve Paylaşım merkezi*nden mevcut ağımızı seçiyor ve *Özellikler*'ine giriyoruz. Aşağıdaki resimde kırmızı kutucuk içine aldığım "**VirtualBox Bridged Networking Driver**" sizde görünmüyor. Bunu yükleyebilmek için aşağıda numaralandırdığım şekilde *Ağ Bağlantınız* &gt; *Özellikler* &gt; *Yükle* &gt; *Hizmet* yolunu izleyip *VirtualBox Bridged Networking Driver* kurulumunu seçmeniz gerekiyor.
![virtualbox-bridged-networking-driver](https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/12/virtualbox-bridged-networking-driver.png)
Sürücü için dosyalara ihtiyaç duyduğunda "*C:\Program Files\Oracle\VirtualBox\drivers\network*" yolundaki dosyaları kullanmanız gerekiyor. Bu işlemlerden sonra *Bridged Adapter* seçebileceksiniz.
Yaptığımız değişiklikleri kaydedip, *VirtualBox*'taki bilgisayarımızı başlattığımızda uzak masaüstü bağlantısı için her şey hazır demektir. *VirtualBox* üzerinde çalışan bilgisayarın adını veya *Bridged Adapter* seçerek verdiğimiz bağlantının özelliklerinden edinebileceğimiz IP adresini yazarak uzak masaüstü bağlantısı yapabiliriz.
![uzak-masaustu-baglantisi](https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/12/uzak-masaustu-baglantisi.png)
