---
title: SharePoint Arama Sonuçlarının Sadece Sistem Hesabına Görünmesi
date: 2014-03-27 15:59
---

Geliştirdiğimiz portalda son ana kadar farketmediğimiz bu hata kısa süreli de olsa bir panik hali yaşamama sebep oldu 🙂 Yeni sorunumuz şu ki arama sonuçları sadece *Sistem Hesabı* kullanıcılarına görünür durumda, diğer tüm kullanıcılar arama sonuçlarında boş sayfa görmekteler.

<!--more-->
Burada öncelikle *Search Service* için kullandığımız hesabın hangisi olduğunu öğrenmemiz gerekiyor. *Central Administration* sayfasında *Manage Service Applications* linkinden ulaşabileceğimiz *Search Service Application*'da "**Default content access account**" karşısında yazan kullanıcıyı, aşağıdaki adımları takip ederek ***Windows Authorization Access Group***'a eklememiz gerekiyor.

1. *Active Directory Users and Computers* uygulamasını açıyoruz.
2. ***Builtin*** altında bulunan ***Windows Authorization Access Group***'a çift tıklıyoruz.
3. ***Members*** sekmesine geçip *Add* butonuna tıklıyoruz.
4. Kullanıcımızı buraya ekleyip, buradaki işimizi tamamlıyoruz.
5. *Central Admin* &gt; *Manage service applications* &gt; *Search Service Application* &gt; *Content Sources* yolunu izleyerek ***Full Crawl* **başlatıyoruz.

Crawl işlemi tamamlandığında, arama sonuçları tüm kullanıcılar tarafından görüntülenebilecek.

İyi çalışmalar...
