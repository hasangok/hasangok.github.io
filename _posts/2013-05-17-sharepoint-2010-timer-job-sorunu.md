---
layout: post
title: Sharepoint 2010 Timer Job Sorunu
date: 2013-05-17 23:16
author: hasangok
comments: true
Tags: [Bilgisayar, Sharepoint, SharePoint, sorun, timer job]
---
<p style="text-align: justify;">Sharepoint üzerinde geliştirme yaptıkça bazı sorunlarla karşılaşıyoruz. Tecrübeli abiler-ablalar artık nasıl alışmışlarsa duruma "<em>Sharepoint yapar öyle, bug vardır.</em>", "<em>Bugün üstüne varma yarına kendiliğinden düzelir.</em>" tarzı cevaplarla beni yatıştırsalar da hala alışamadığım noktalar var ki bir tanesini sizlerle paylaşmak için geçtim yine bilgisayarımın başına.</p>
<p style="text-align: justify;">"<em><strong>Timer Job</strong></em>" dediğimiz şey, adı üstünde zamanlanmış bir görev oluyor. Belirlediğimiz zaman aralıklarında çalışarak bizim kendisine yüklediğimiz görevleri yerine getirip, tekrar çalışıncaya dek susuyor. Ben de 20 dakikada bir çalışarak tarihi geçmiş duyuruları kontrol eden ve hem bu işin logunu tutan hem de duyurudaki ilgili kişiye e-posta ile bildim yapan basit bir timer job oluşturdum. Oluşturdum ama oluşturana kadar hayattan soğudum desem yalan söylemiş olmam :)</p>
<p style="text-align: justify;"><!--more--></p>
<p style="text-align: justify;">Problem şu ki, projemi sunucuya deploy ediyorum ve yazdıklarım işlemeye başlıyor. Ancak deneme-yanılma yoluyla sık sık yanıldığım için ve yazdığımız göreve yeni özellikler eklememiz istendiği için sürekli olarak kodda değişiklikler yapıp bunun yeni çalışan halini test etmem gerekiyor. Buradaki ilk sorunum (ya da ilk sorum diyeyim, ilk öğrendiğim) koda koyduğum breakpointlerde nasıl duracağım ve debug moduna gireceğimdi. Oldukça basitmiş: <strong>Debug</strong> menüsünden "<strong>Attach to Process</strong>" diyoruz ve listeden "<em><strong>OWSTIMER.EXE</strong></em>" seçiyoruz.</p>
<p style="text-align: center;"><a href="http://www.hasangok.com.tr/wp-content/uploads/2013/05/attach-to-process-owstimer.png"><img class="size-full wp-image-70 aligncenter" src="http://www.hasangok.com.tr/wp-content/uploads/2013/05/attach-to-process-owstimer.png" alt="Attach to process" width="738" height="500" /></a></p>
<p style="text-align: justify;">Beni asıl çıldırtan sorun şuydu: Üzerinde ne kadar değişiklik yaparsam yapayım, ne kadar deploy edersem edeyim, <em>son yazdığım kodlar bir şekilde yok oluyor ve timer job’ın ilk yazdığım hali çalışıyordu</em>. "<em>Bu Timer Job’dan zaten var, üzerine yazayım mı?</em>" sorusuna evet dediğim halde yaptığım güncellemeler yansımıyordu. Bu noktada takılıp kalmışken sağolsun Yavuz imdadıma yetişti ve yapmam gerekenleri söyledi:</p>

<ol>
	<li style="text-align: justify;">C:\Windows\assembly klasöründe yazdığımız timer job’a ait class’ın ismini bulup sileceğiz.<a href="http://www.hasangok.com.tr/wp-content/uploads/2013/05/assembly-folder.png"><img class="aligncenter size-full wp-image-71" src="http://www.hasangok.com.tr/wp-content/uploads/2013/05/assembly-folder.png" alt="assembly-folder" width="737" height="500" /></a></li>
	<li style="text-align: justify;">Yönetimsel Araçlar &gt; Servisler bölümünden Sharepoint Timer servisini yeniden başlatacağız.<a href="http://www.hasangok.com.tr/wp-content/uploads/2013/05/sharepoint-timer.png"><img class="aligncenter size-full wp-image-72" src="http://www.hasangok.com.tr/wp-content/uploads/2013/05/sharepoint-timer.png" alt="sharepoint-timer" width="820" height="600" /></a></li>
</ol>
<p style="text-align: justify;">Bu işlemlerden sonra projemizi deploy ettiğimizde, yazdığımız neyse o çalışmaya başlıyor. Bu sıkıntıyı da böylece çözmüş oluyor ve rahatlıyoruz.</p>
