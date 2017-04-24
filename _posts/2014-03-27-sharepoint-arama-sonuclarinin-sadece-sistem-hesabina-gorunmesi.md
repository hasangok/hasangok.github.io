---
layout: post
title: SharePoint Arama Sonuçlarının Sadece Sistem Hesabına Görünmesi
date: 2014-03-27 15:59
author: hasangok
comments: true
Tags: [Full Crawl, Search Service, Sharepoint, SharePoint, System Account]
---
<p style="text-align: justify;">Geliştirdiğimiz portalda son ana kadar farketmediğimiz bu hata kısa süreli de olsa bir panik hali yaşamama sebep oldu :) Yeni sorunumuz şu ki arama sonuçları sadece <em>Sistem Hesabı</em> kullanıcılarına görünür durumda, diğer tüm kullanıcılar arama sonuçlarında boş sayfa görmekteler.</p>
<p style="text-align: justify;">Burada öncelikle <em>Search Service</em> için kullandığımız hesabın hangisi olduğunu öğrenmemiz gerekiyor. <em>Central Administration</em> sayfasında <em>Manage Service Applications</em> linkinden ulaşabileceğimiz <em>Search Service Application</em>'da "<strong>Default content access account</strong>" karşısında yazan kullanıcıyı, aşağıdaki adımları takip ederek <strong><em>Windows Authorization Access Group</em></strong>'a eklememiz gerekiyor.</p>

<ol style="text-align: justify;">
	<li><em>Active Directory Users and Computers</em> uygulamasını açıyoruz.</li>
	<li><em><strong>Builtin</strong></em> altında bulunan <em><strong>Windows Authorization Access Group</strong></em>'a çift tıklıyoruz.</li>
	<li><em><strong>Members</strong></em> sekmesine geçip <em>Add</em> butonuna tıklıyoruz.</li>
	<li>Kullanıcımızı buraya ekleyip, buradaki işimizi tamamlıyoruz.</li>
	<li><em>Central Admin</em> &gt; <em>Manage service applications</em> &gt; <em>Search Service Application</em> &gt; <em>Content Sources</em> yolunu izleyerek <strong><em>Full Crawl</em> </strong>başlatıyoruz.</li>
</ol>
<p style="text-align: justify;">Crawl işlemi tamamlandığında, arama sonuçları tüm kullanıcılar tarafından görüntülenebilecek.</p>
<p style="text-align: justify;">İyi çalışmalar...</p>
