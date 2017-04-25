---
layout: post
title: Sharepoint 2010 Timer Job Sorunu
date: 2013-05-17 23:16
author: hasangok
comments: true
Tags: [Bilgisayar, Sharepoint, SharePoint, sorun, timer job]
---
Sharepoint üzerinde geliştirme yaptıkça bazı sorunlarla karşılaşıyoruz. Tecrübeli abiler-ablalar artık nasıl alışmışlarsa duruma "*Sharepoint yapar öyle, bug vardır.*", "*Bugün üstüne varma yarına kendiliğinden düzelir.*" tarzı cevaplarla beni yatıştırsalar da hala alışamadığım noktalar var ki bir tanesini sizlerle paylaşmak için geçtim yine bilgisayarımın başına.
"***Timer Job***" dediğimiz şey, adı üstünde zamanlanmış bir görev oluyor. Belirlediğimiz zaman aralıklarında çalışarak bizim kendisine yüklediğimiz görevleri yerine getirip, tekrar çalışıncaya dek susuyor. Ben de 20 dakikada bir çalışarak tarihi geçmiş duyuruları kontrol eden ve hem bu işin logunu tutan hem de duyurudaki ilgili kişiye e-posta ile bildim yapan basit bir timer job oluşturdum. Oluşturdum ama oluşturana kadar hayattan soğudum desem yalan söylemiş olmam :)

Problem şu ki, projemi sunucuya deploy ediyorum ve yazdıklarım işlemeye başlıyor. Ancak deneme-yanılma yoluyla sık sık yanıldığım için ve yazdığımız göreve yeni özellikler eklememiz istendiği için sürekli olarak kodda değişiklikler yapıp bunun yeni çalışan halini test etmem gerekiyor. Buradaki ilk sorunum (ya da ilk sorum diyeyim, ilk öğrendiğim) koda koyduğum breakpointlerde nasıl duracağım ve debug moduna gireceğimdi. Oldukça basitmiş: **Debug** menüsünden "**Attach to Process**" diyoruz ve listeden "***OWSTIMER.EXE***" seçiyoruz.
![Attach to process](https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/05/attach-to-process-owstimer.png)
Beni asıl çıldırtan sorun şuydu: Üzerinde ne kadar değişiklik yaparsam yapayım, ne kadar deploy edersem edeyim, *son yazdığım kodlar bir şekilde yok oluyor ve timer job’ın ilk yazdığım hali çalışıyordu*. "*Bu Timer Job’dan zaten var, üzerine yazayım mı?*" sorusuna evet dediğim halde yaptığım güncellemeler yansımıyordu. Bu noktada takılıp kalmışken sağolsun Yavuz imdadıma yetişti ve yapmam gerekenleri söyledi:

1. C:\Windows\assembly klasöründe yazdığımız timer job’a ait class’ın ismini bulup sileceğiz.
![assembly-folder](https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/05/assembly-folder.png)
2. Yönetimsel Araçlar &gt; Servisler bölümünden Sharepoint Timer servisini yeniden başlatacağız.
![sharepoint-timer](https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/05/sharepoint-timer.png)

Bu işlemlerden sonra projemizi deploy ettiğimizde, yazdığımız neyse o çalışmaya başlıyor. Bu sıkıntıyı da böylece çözmüş oluyor ve rahatlıyoruz.
