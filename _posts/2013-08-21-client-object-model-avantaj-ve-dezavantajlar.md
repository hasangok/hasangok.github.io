---
layout: post
title: Client Object Model - Avantaj ve Dezavantajlar
date: 2013-08-21 15:43
author: hasangok
comments: true
Tags: [Client Object Model, Sharepoint, SharePoint]
---
<p style="text-align: justify;">Üzerinde çalıştığım son birkaç projedir <em>Client Object Model</em> kullanıyorum. Bugün ofiste böyle bir tartışma da çıkınca blogumda yer vermek istedim. İşte <em>Client Object Model</em>'in avantaj ve dezavantajları.</p>
<p style="text-align: justify;"><strong>Avantajlar:</strong></p>

<ol style="text-align: justify;">
	<li style="text-align: justify;"><em>JavaScript</em> kullanılarak kullanıcı tarafındaki web tarayıcısından <em>SharePoint</em> verilerine ulaşabiliyoruz.</li>
	<li style="text-align: justify;"><em>jQuery</em> yardımıyla zengin kullanıcı arayüzü olan web partlar geliştirebiliriz.</li>
	<li style="text-align: justify;">Visual Studio'ya gerek duymaksızın, sadece web tarayıcısı üzerinden, <em>İçerik Düzenleyicisi</em> web partı kullanarak istediğimiz web partları geliştirme şansına sahip oluruz.</li>
	<li style="text-align: justify;">Sitenizi şablon olarak kaydedip başka bir yere aktardığınızda, <em>Client Object Model</em> ile geliştirdiğiniz her şey de aktardığınız tarafta hazır bulunur.</li>
	<li style="text-align: justify;"><em>Client Object Model</em> kullanarak geliştirdiğiniz web partların çalışır hale gelmesi için deploy ya da iisreset gerekmez.</li>
	<li style="text-align: justify;">Geliştirme yapmak istediğiniz bilgisayarda <em>SharePoint</em>'in yüklü bulunması gerekmez.</li>
</ol>
<p style="text-align: justify;"><strong>Dejavantajlar:</strong></p>

<ol>
	<li style="text-align: justify;">Sunucu tarafında ihtiyaç duyduğumuz zaman yazdığımız <em>RunWithElevatedPrivilege</em> (burada bahsetmiştim) tarzı bir metod kullanma şansımız yok. Dolayısıyla sadece iznimiz kadar bilgiye ulaşabiliyoruz.</li>
	<li style="text-align: justify;"><em>Client Object Model</em>'de <em>SharePoint</em> verilerine ulaşmak için kullanabileceğimiz oldukça sınırlı sayıda sınıf var. Örneğin <em>User Profile</em> bilgilerine erişmemiz mümkün değil (<em>jQuery</em> ile <em>SharePoint</em> web servislerini kullanarak bu işlemi yapabiliyoruz).</li>
	<li style="text-align: justify;">Üzerinde çalıştığımız site collection'dan başka bir site collection üzerindeki veriye ulaşamıyoruz.</li>
	<li style="text-align: justify;">Ulaşmak istediğimiz veriler biraz gecikmeli gelebiliyor. Bu yüzden anlık sorgulama yapmamız gereken durumlarda (örneğin <a title="Enerjisa – Enerjik Sözlük" href="http://www.hasangok.com.tr/?portfolio=enerjisa-enerjik-sozluk">burada</a>) sorunlar yaşanabiliyor.</li>
</ol>
