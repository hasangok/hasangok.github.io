---
title: Faydalı Bilgi - Masaüstü Klasörünün Konumunu Değiştirebilirsiniz
date: 2010-06-07 00:30
---

"Bir gece ansızın Windows'unuz çökebilir! Buna hazır mısınız?" sorusuyla başlayayım yazıya 🙂 Bilgisayarınızda sakladığınız belgeler gerçekten güvende mi? En azından işletim sisteminiz açılmadığında dosyalarınızı kurtarabilecek durumda mısınız?

<!--more-->
Windows'un durduk yere yamuk yapma ihtimaline karşı "Belgeler, Resimler, Videolar, Müzikler vs." gibi gklasörleri Windows'un kurulu olduğu sürücüde saklamam. Böylece işletim sistemini çökerttiğimde ya da o benim yerime kendi kendini çökerttiğinde format atmaktan çekinmiyorum. Daha doğrusu çekinmiyordum. Ta ki masaüstümde de can alıcı dosyaları kaybetmenin eşiğine gelinceye kadar!

![masaustu](/uploads/2010/06/masaustu.jpg)

Gelen e-postaların eklentileri, internetten bulduğum faydalı bilgiler, e-kitaplar, ders notları, yazdığım programcıklar vb. sık sayılabilecek aralıklarla kullandığım herşeyi masaüstüne atar oldum. O kadar ki, masaüstüm zaman zaman yukarıdakine benziyor. Bu dosyaları bir süre masaüstümde bekletir ve daha az kullanılır olduğum zaman ilgili klasörlere aktarırım. Ama geçen gün yaşadığım talihsiz olayla masaüstümdeki dosyalarımı her an kaybedebileceğim gerçeğiyle yüzleştim ve karar verdim: Windows kurduğun sürücüde önemli dosyalarını saklamayacaksın!

Masaüstünü dosyalarla doldurup taşırma alışkanlığımdan da vazgeçemeyeceğim için bu klasörü başka bir sürücüye taşıyabilecek miyim diye baktım. Evet taşıyabiliyormuşum 🙂 Nasıl oluyor o iş bahsedelim.

Windows XP'de masaüstü klasörünün konumu "C:\Documents and Settings\Kullanıcı Adı\Desktop", Windows Vista ve Windows 7'de "C:\Users\Kullanıcı Adı\Desktop" şeklindedir. Benim istediğim ise bunu D:\Masaüstü gibi başka bir sürücüdeki klasörde saklamak. Bunu yapmak için:

* Çalıştır'a ya da başlat menüsündeki program arama bölümüne regedit yazıp kayıt düzenleyicisini açalım.
* "HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\User Shell Folders" sırasını takip edip "Desktop" dizesinin değerine, masaüstünüzü koymak istediğimiz klasörün konumunu yazalım. ("%USERPROFILE%\Desktop" yerine "D:\Masaüstü" gibi birşey yazacaksınız.)

Bilgisayarınızı yeniden başlattığınızda masaüstüne kaydettiğiniz herşey "D:\Masaüstü" klasörüne gidecek. Windows sizi format atmaya zorladığında "Acaba masaüstünde gerekli birşey var mıydı?" diye düşünmenize gerek kalmayacak.

Sözün özü: "Eşeği sağlam kazığa bağlayın." diyorum 🙂  
Selametle...
