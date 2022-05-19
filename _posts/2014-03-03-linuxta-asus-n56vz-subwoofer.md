---
title: Linux'ta ASUS N56VZ SubWoofer
date: 2014-03-03 10:53
---

Biliyorum, siz de benim gibi bas sesleri almadığınızda dinlediğiniz müzikten zevk alamıyorsunuz 😉 O halde Linux kurulu bilgisayarınızda bu mini woofer'ı aktif etmek için şu dosyayı yönetici olarak düzenleyin:

<!--more-->
```
/etc/modprobe.d/alsa-base.conf
```
Bu dosyanın en alt satırına inip aşağıdaki satırı eklediğimizde, woofer'ımız aktif olacak:

```
options snd-hda-intel model=asus-mode4
```
İyi eğlenceler...
