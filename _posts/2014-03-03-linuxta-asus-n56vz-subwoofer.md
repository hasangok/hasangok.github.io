---
layout: post
title: Linux'ta ASUS N56VZ SubWoofer
date: 2014-03-03 10:53
author: hasangok
comments: true
Tags: [Asus N56VZ, Bilgisayar, Linux, Subwoofer]
---
<p style="text-align: justify;">Biliyorum, siz de benim gibi bas sesleri almadığınızda dinlediğiniz müzikten zevk alamıyorsunuz ;) O halde Linux kurulu bilgisayarınızda bu mini woofer'ı aktif etmek için şu dosyayı yönetici olarak düzenleyin:</p>

<pre class="lang:default decode:true">/etc/modprobe.d/alsa-base.conf</pre>
<p style="text-align: justify;">Bu dosyanın en alt satırına inip aşağıdaki satırı eklediğimizde, woofer'ımız aktif olacak:</p>

<pre class="lang:default decode:true">options snd-hda-intel model=asus-mode4</pre>
<p style="text-align: justify;">İyi eğlenceler...</p>
