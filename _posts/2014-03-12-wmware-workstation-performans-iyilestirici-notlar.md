---
title: WMware Workstation Performans İyileştirici Notlar
date: 2014-03-12 10:00
---

![wmware-workstation-logo](/uploads/2014/03/wmware-workstation-logo.png "wmware-workstation-logo")

Neden yaptım bilmiyorum, *VirtualBox*'tan vazgeçip *WMWare Workstation* kullanmaya başlayalı yüzüm gülmedi 🙂 Ürünü tanımadığımdan olsa gerek, oluşturduğum sanal bilgisayara müthiş diyebileceğim donanım ayırsam da (i7 işlemciden 2 çekirdek, 12 GB RAM, SSD disk üzerinde harddisk alanı gibi) istediğim performansı bir türlü alamadım. Son olarak aşağıda sıraladığım birkaç değişiklikiği yapınca sanal bilgisayarımın performans düzeyi tahammül edilebilecek düzeye geldi. VirtualBox'a geri mi dönsem diye düşünürken bu notları sizlerle de paylaşmak istedim:

<!--more-->
1. "C:\ProgramData\VMware\VMware Workstation" dizini altında bulacağınız **settings.ini** dosyasına aşağıdaki satırı ekleyerek ***.vmem*** uzantılı swap dosyalarını devre dışı bırakabilirsiniz:
```
mainMem.useNamedFile = "FALSE"
```
2. Sanal bilgisayarlarınız için log dosyaları oluşturmaktan vazgeçin. Bunun için oluşturduğunuz sanal bilgisayarın ***.vmx*** uzantılı dosyasını düzenleyip aşağıdaki satırı ekleyebilirsiniz:
```
logging = "FALSE"
```

3. Unity modunu devre dışı bırakın. Bunun için yine ***.vmx*** dosyanızı açıp aşağıdaki satırları ekleyebilirsiniz:
```
isolation.tools.unity.disable="TRUE"
unity.allowCompositingInGuest="FALSE"
unity.enableLaunchMenu = "FALSE"
unity.showBadges = "FALSE"
unity.showBorders = "FALSE"
unity.wasCapable = "FALSE"
```

4. Disk ve bellek I/O performanslarını iyileştirmek için aşağıdaki satırları ekleyebilirsiniz:
```
MemTrimRate = "0"
sched.mem.pshare.enable = "FALSE"
snapshot.disabled = "TRUE"
MemAllowAutoScaleDown = "FALSE"</pre>
```

Umarım bu düzenlemelerden sonra çalışılabilir bir ortam sahibi olursunuz.

İyi çalışmalar...
