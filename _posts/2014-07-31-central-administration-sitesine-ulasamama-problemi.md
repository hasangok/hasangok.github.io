---
layout: post
title: Central Administration Sitesine Ulaşamama Problemi
date: 2014-07-31 17:40
author: hasangok
comments: true
Tags: [Central Administration, Sharepoint, SharePoint]
---
<p style="text-align: justify;">Bugün yine canımız cananımız <em>SharePoint</em>'in bir sorunuyla karşılaşıp çözümünü tecrübe ettiğim için not etmek istedim.</p>
<p style="text-align: justify;">2 adet <em>SharePoint</em> sunucusu bulunan farmımızdan, bu sunuculardan bir tanesini çıkarmamız gerekti. Her iki sunucu üzerinde de <em>Central Administration</em> (kısaca <em>CA</em>) sitesi bulunuyordu, ancak <em>CA</em> sitesine ulaştığımız adres (url) farmdan çıkaracağımız servera işaret ediyordu. Farmda kalacak sunucu üzerinde de <em>Central Administration</em> bulunduğundan ve çıkarma işlemini "<strong>SharePoint 2010 Products Configuration Wizard</strong>" ile yapacağımızdan, iç taraftaki güncellemeleri <em>SharePoint</em> yapacaktır diye düşünmüştüm. Tabi ki yanılmışım :)</p>
<p style="text-align: justify;"><!--more--></p>
<p style="text-align: justify;">Sunucuyu farmdan çıkardıktan sonra artık <em>CA</em> sitesine ulaşılamıyordu. Sorunu çözmek için aşağıdaki yolu izleyebiliriz:</p>

<ol style="text-align: justify;">
	<li>Farmda kalan sunucuda <em>SharePoint 2010 Products Configuration Wizard</em>'ı çalıştırıp ilerlerken <strong>Host Central Administration Web Application</strong> başlığına geldiğimizde aşağıdaki ekran görüntüsündeki gibi "<em>Use this machine to host the web site</em>" seçiyoruz.
<img class="aligncenter size-full wp-image-744" src="http://www.hasangok.com.tr/wp-content/uploads/2014/07/Use-this-machine-to-host-the-web-site.jpg" alt="Use-this-machine-to-host-the-web-site" width="620" height="529" /></li>
	<li><em>SharePoint 2010 Products Configuration Wizard</em> başarıyla tamamlandığında <em>CA</em> sitesinin url'ini başarıyla güncellediğini görüyoruz. Ancak <em>Finish</em>'e tıkladığımızda halen eski url'i açmaya çalışıyor. Aynı şekilde başlat menüsündeki <em>Central Administration</em> linki de bizi eski sunucuya göndermeye çalışıyor. Daha enteresan olanı tarayıcımızda <em>http://yenisunucu:yeniport</em> şeklinde ulaşırsak sayfa görüntülenemezken, <em>http://yenisunucu:yeniport/default.aspx</em> şeklinde yazdığımızda sayfaya ulaşabiliyor.</li>
	<li>Bu aşamada <em>default.aspx</em> ile birlikte <em>CA</em> sitemizi görüntüleyip <em>System Settings</em> &gt; <em>Configure Alternate Access Mappings</em> bölümüne geçiyoruz. <em>CA</em> için oluşturulmuş ve eski sunucuyu işaret eden kayıtları düzenleyip, eski url'leri yenileriyle değiştirip kaydediyoruz.</li>
	<li>Bu aşamada herşeyin tamamlanmış olmasını bekliyoruz. Evet, kontrol ediyoruz... Tabi ki halen eski sunucuya yönlendiriliyoruz :) Şimdi de <strong>regedit.exe</strong> programını çalıştırıp şu yolu izliyoruz:
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Shared Tools\Web Server Extensions\14.0\WSS\
Buradaki <strong>CentralAdministrationURL</strong> değerini <em>http://yenisunucu:yeniport/</em> şeklinde değiştirip kaydediyoruz.</li>
</ol>
<p style="text-align: justify;">Artık <em>CA</em> sitesi yeni adresinden ve tüm linkler aracılığıyla erişilebilir durumda.</p>
<p style="text-align: justify;">İyi çalışmalar.</p>
