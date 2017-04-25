---
layout: post
title: İlk Bakışta Windows 8.1
date: 2013-10-20 23:59
author: hasangok
comments: true
Tags: [Bilgisayar, Programlar, Windows 8, Windows 8.1]
---
<p style="text-align: justify;">Çok merak ediyormuşsunuz gibi dün <a title="Windows 8.1 Güncellemesi" href="http://www.hasangok.com.tr/403/windows-8-1-guncellemesi.html">buradan</a> duyurmuştum Windows 8.1'e güncellediğimi. İlk bakışta gözüme çarpanları ve izlenimlerimi sizlere aktarmak için tekrar yazmak istedim.</p>

<ol style="text-align: justify;">
	<li>Güncellemeyi <em>Windows 8 Mağazası</em> üzerinden yapmak zorundasınız, herhangi bir <em>ISO</em> dosyası bulunmuyor.</li>
	<li>İşlem oldukça uzun sürüyor. İndirme işleminizi duraklatıp bilgisayarınızı kapatabilirsiniz. Bilgisayarınızı yeniden açıp tekrar indir dediğinizde, indirme işlemi kaldığı yerden devam ediyor.</li>
	<li><em>Windows 8</em>'de yerel hesap kullanıyordum, 8.1 güncellemesinden sonra <em>Microsoft hesabı</em> ile oturum açmanız isteniyor. Yerel hesap ile kesinlikle bilgisayarınızı açamıyorsunuz. Daha sonra bir yerel hesap oluşturup Microsoft hesabını kaldırmanız mümkün. Ancak böyle bir şey yapmanın gerekliliği tartışılır.</li>
	<li>Başlangıç ekranındaki kutucukların renklendirmesi, ilgili uygulamanın ikonunun rengine göre belirleniyor. Bu da rengarenk bir başlangıç ekranı demek oluyor. Renk değişimini çok hoş buldum, eskisinden çok daha güzel. Buyrun görelim:
<a href="https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/10/windows-8.1-desktop.png"><img class="aligncenter size-full wp-image-411" alt="windows-8.1-desktop" src="https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/10/windows-8.1-desktop.png" width="1920" height="1080" /></a></li>
	<li><em>Windows 8</em>'de olmayan <em>başlat tuşu</em> geri gelmiş, başlangıç ekranını açıyor. Pratikte hiçbir değişiklik yok anlayacağınız. Ancak eski bir dostu görmek de hoş.</li>
	<li>Birden fazla monitör kullanıyorsanız, <em>Windows 8.1</em> farklı monitörler için farklı <strong><em>dpi</em></strong> değerleri seçiyor, bazı programlarda ölçekleme problemleri yaşadım. Düzeltmek için şu yolu izleyebilirsiniz:
<ol>
	<li><em>Masaüstü</em>ne sağ tıklayıp <strong>Kişiselleştir</strong>'i seçin.</li>
	<li>Sol alt kısımda bulunan "<em>Ayrıca bkz.</em>" bölümünden <strong>Görüntü</strong>'ye tıklayın.</li>
	<li>"<em>Tüm görüntülerim için bir ölçekleme düzeyi seçmeme izin ver</em>" kutucuğunu işaretleyin.</li>
	<li>Bilgisayarınızı yeniden başlatın.</li>
	<li>Görüntülerin ölçeklenmesiyle ilgili bir probleminiz kalmayacaktır.</li>
</ol>
</li>
	<li><em>Microsoft hesabı</em> ile oturum açtığınızdan, bilgisayarınızı her açtığınızda bu hesabınızın parolasını girmeniz isteniyor. Bunu şöyle aşabiliyoruz:
<ol>
	<li>Başlangıç ekranına "<strong>netplwiz</strong>" yazıp çalıştırın.</li>
	<li>"<em>Kullanıcı bu bilgisayarı kullanmak için bir ad ve parola girmelidir</em>" kutucuğu önündeki işareti kaldırın.</li>
	<li><strong>Uygula</strong> veya <strong>Tamam</strong> dediğimizde gelen parola isteyen pencereye <strong>Microsoft hesabımızın parolasını girmeliyiz</strong>! Boş bırakıp kaydedersek oturum açarken hatalı parola diyecektir.</li>
	<li>Ne kadar güvenilir olduğu tartışılır ancak o veya bu şekilde bir çözüm olarak kullanılabilir. Artık otomatik olarak oturum açabilirsiniz.</li>
</ol>
</li>
	<li><strong>Bilgisayar</strong>ımızın adı "<em>Bu Bilgisayar</em>" olarak değişmiş. Artık sadece diskleri değil, <em>Belgeler</em>, <em>Müzikler</em> vb. gibi kütüphanelerimizin klasörlerini de gösteriyor. Bunları görmek istemiyorsanız şu adımları izleyebilirsiniz:
<ol>
	<li>Başlangıç ekranına "<strong>regedit</strong>" yazıp <em>Kayıt Düzenleyicisi</em>ni açın.</li>
	<li><strong>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Current Version\explorer\MyComputer\NameSpace</strong> yolunu izleyin, ve aşağıdaki anahtarları silin.</li>
	<li>{1CF1260C-4DD0-4ebb-811F-33C572699FDE} : <em>Müzikler</em> Klasörü
{374DE290-123F-4565-9164-39C4925E467B} : <em>İndirilenler</em> Klasörü
{3ADD1653-EB32-4cb0-BBD7-DFA0ABB5ACCA} : <em>Resimler</em> Klasörü
{A0953C92-50DC-43bf-BE83-3742FED03C9C} : <em>Videolar</em> Klasörü
{A8CDFF1C-4878-43be-B5FD-F8091C1C60D0} : <em>Bekgeler</em> Klasörü
{B4BFCC3A-DB2C-424C-B029-7FE99A87C641} : <em>Masaüstü</em>.</li>
</ol>
</li>
	<li>Başlangıç ekranı yerine direk masaüstüne düşmek istiyorsanız <em>Görev Çubuğu</em>nda sağ tıklayıp <em>Özellikler</em>'i seçtikten sonra, <em>Gezinti</em> sekmesinden "<em>Oturum açtığımda veya bir ekrandaki tüm uygulamaları kapattığımda Başlangıç yerine masaüstüne git</em>" kutucuğunu işaretleyebilirsiniz. Başlangıç ekranına alışmanız ise tavsiyemdir, doğru organize ettiğinizde daha kullanışlı olduğunu düşünüyorum.</li>
</ol>
<p style="text-align: justify;">Yukarıdaki problemler ilk an canımı sıksa da kolayca düzeltilebilir olduklarından olumsuz herhangi bir izlenimim yok. Zaten Windows 8'e iyice alışmışken yeniliklerinden de uzak kalmamak gerekir diye düşünüyor ve size de güncel kalmanızı tavsiye ediyorum.</p>
<p style="text-align: justify;">Kalın sağlıcakla...</p>
