---
layout: post
title: WMware Workstation Performans İyileştirici Notlar
date: 2014-03-12 10:00
author: hasangok
comments: true
Tags: [Bilgisayar, performans, Programlar, WMware Workstation]
---
<p style="text-align: justify;"><img class="alignleft  wp-image-614" style="margin: 2px; border: 0px;" alt="wmware-workstation-logo" src="https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2014/03/wmware-workstation-logo.png" width="154" height="154" />Neden yaptım bilmiyorum, <em>VirtualBox</em>'tan vazgeçip <em>WMWare Workstation</em> kullanmaya başlayalı yüzüm gülmedi :) Ürünü tanımadığımdan olsa gerek, oluşturduğum sanal bilgisayara müthiş diyebileceğim donanım ayırsam da (i7 işlemciden 2 çekirdek, 12 GB RAM, SSD disk üzerinde harddisk alanı gibi) istediğim performansı bir türlü alamadım. Son olarak aşağıda sıraladığım birkaç değişiklikiği yapınca sanal bilgisayarımın performans düzeyi tahammül edilebilecek düzeye geldi. VirtualBox'a geri mi dönsem diye düşünürken bu notları sizlerle de paylaşmak istedim:</p>

<ol style="text-align: justify;">
	<li>"C:\ProgramData\VMware\VMware Workstation" dizini altında bulacağınız <strong>settings.ini</strong> dosyasına aşağıdaki satırı ekleyerek <em><strong>.vmem</strong></em> uzantılı swap dosyalarını devre dışı bırakabilirsiniz:
<pre class="lang:default decode:true">mainMem.useNamedFile = "FALSE"</pre>
</li>
	<li>Sanal bilgisayarlarınız için log dosyaları oluşturmaktan vazgeçin. Bunun için oluşturduğunuz sanal bilgisayarın <em><strong>.vmx</strong></em> uzantılı dosyasını düzenleyip aşağıdaki satırı ekleyebilirsiniz:
<pre class="lang:default decode:true">logging = "FALSE"</pre>
</li>
	<li>Unity modunu devre dışı bırakın. Bunun için yine <em><strong>.vmx</strong></em> dosyanızı açıp aşağıdaki satırları ekleyebilirsiniz:
<pre class="lang:default decode:true">isolation.tools.unity.disable="TRUE"
unity.allowCompositingInGuest="FALSE"
unity.enableLaunchMenu = "FALSE"
unity.showBadges = "FALSE"
unity.showBorders = "FALSE"
unity.wasCapable = "FALSE"</pre>
</li>
	<li>Disk ve bellek I/O performanslarını iyileştirmek için aşağıdaki satırları ekleyebilirsiniz:
<pre class="lang:default decode:true">MemTrimRate = "0"
sched.mem.pshare.enable = "FALSE"
snapshot.disabled = "TRUE"
MemAllowAutoScaleDown = "FALSE"</pre>
</li>
</ol>
<p style="text-align: justify;">Umarım bu düzenlemelerden sonra çalışılabilir bir ortam sahibi olursunuz.</p>
<p style="text-align: justify;">İyi çalışmalar...</p>
