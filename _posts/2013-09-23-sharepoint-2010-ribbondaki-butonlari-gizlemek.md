---
layout: post
title: SharePoint 2010 - Ribbon'daki Butonları Gizlemek
date: 2013-09-23 16:29
author: hasangok
comments: true
Tags: [Buton Gizlemek, Ribbon, Sharepoint, SharePoint]
---
<p style="text-align: justify;"><img class="alignleft  wp-image-342" alt="SharePoint2010" src="https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/09/SharePoint2010.jpg" width="138" height="107" /><em>SharePoint 2010</em>'da herhangi bir liste ya da kütüphanenin ribbon menüsündeki çeşitli butonları gizlemeye ihtiyacımız olabiliyor. Son çalışmam, belirli bir listedeki "<strong>Create View</strong>" (<em>Görünüm Oluştur</em>), ve "<strong>Modify View</strong>" (<em>Görünümü Özelleştir</em>) butonlarının Ribbon'dan kaldırılması yönündeydi. Bunun için bir "<strong>feature</strong>" (özellik) hazırlamam istendi, böylece bu fonksiyon "<strong>Manage Site Feeatures</strong>" (<em>Site Özelliklerini Yönet</em>) altından aktif/pasif durumuna geçebilecekti. Ben bu yazımda hem sitemizdeki tüm listeler/kütüphaneler için geçerli olacak ve sadece <em>XML</em> dosyalarıyla hazırlanabilecek bir özellik oluşturmayı, hem de <em>Visual Studio 2010</em> kullanarak sadece istediğimiz listelerde geçerli olacak bir özellik oluşturmayı anlatmaya çalışacağım.</p>
<p style="text-align: justify;"><strong>A) Butonun Tüm Liste veya Kütüphanelerden Kaldırılması</strong></p>
<p style="text-align: justify;">2 adet <em>XML</em> dosyası ile oluşturabileceğimiz bu özellik için şu dizinde yeni bir klasör oluşturmamız gerekiyor: "<em>C:\Program Files\Common Files\Microsoft Shared\Web Server Extensions\14\TEMPLATE\FEATURES</em>". Yazıma, klasör adını "<strong>DisableRibbonButton</strong>" olarak belirlediğiniz varsayımıyla devam edeceğim. Şimdi <em>DisableRibbonButton</em> klasörü içinde "<em><strong>feature.xml</strong></em>" adlı bir dosya oluşturup içeriğini aşağıdakiyle değiştiriyoruz:</p>
<p style="text-align: justify;">
<pre class="brush: xml;">
<?xml version="1.0" encoding="utf-8" ?>
<Feature Id="33057CD9-6D14-45c9-81AD-5C1FE066AC75"
         Title="DisableRibbonButton"
         Description="DisableRibbonButton"
         Version="1.0.0.0"
         Scope="Web"
         xmlns="http://schemas.microsoft.com/sharepoint/">
  <ElementManifests>
    <ElementManifest Location="Manifest.xml" />
  </ElementManifests>
</Feature>
</pre>
</p>
<p style="text-align: justify;">Ardından "<em><strong>Manifest.xml</strong></em>" adlı başka bir dosya oluşturup içeriğini aşağıdakiyle değiştiriyoruz:</p>
<p style="text-align: justify;">
<pre class="brush: xml;">
<?xml version="1.0" encoding="utf-8"?>
<Elements xmlns="http://schemas.microsoft.com/sharepoint/">
  <CustomAction
    Id="RemoveCreateViewButton"
    Location="CommandUI.Ribbon"
    RegistrationType="List"
    RegistrationId="100">
    <CommandUIExtension>
      <CommandUIDefinitions>
        <CommandUIDefinition
          Location="Ribbon.List.CustomViews.CreateView" />
      </CommandUIDefinitions>
    </CommandUIExtension>
  </CustomAction>
</Elements>
</pre>
</p>
<p style="text-align: justify;"><em>Manifest.xml</em> dosyasında önemli iki nokta var. Bunlardan ilki <strong>RegistrationId</strong> kısmı. Burada özelliğimiz nerede çalışacak onu belirliyoruz. Benim kullanıdığım 100 özel listeleri belirtirken, 101 Döküman Kütüphanesini belirtiyor. Diğer liste ve kütüphaneler için detaylı bilgiye <a href="http://msdn.microsoft.com/en-us/library/microsoft.sharepoint.splisttemplatetype.aspx" target="_blank">bu sayfa</a>dan ulaşabilirsiniz. İkinci önemli kısmı ise <em>CommandUIDefinition</em> altındaki <strong>Location</strong> değeri. Burada hangi butonun gizleneceğini belirtmiş oluyoruz ki her bir buton için Location değerlerini bulabileceğiniz listeye <a href="http://msdn.microsoft.com/en-us/library/ee537543.aspx" target="_blank">buraya</a> tıklayarak ulaşabilirsiniz.</p>
<p style="text-align: justify;">Bu iki dosyayı belirtilen yolda oluşturduğumuz klasör altında oluşturduğumuza göre özelliğimiz hazır demektir. Şimdi bunu sitemize yükleyip aktifleştirmemiz gerekiyor.</p>
<p style="text-align: justify;"><em>Install-SPFeature DisableRibbonButton
Enable-SPFeature DisableRibbonButton –url http://&lt;server_adresi&gt;</em></p>
<p style="text-align: justify;">Tüm bu işlemlerden sonra "<strong>Create View</strong>" butonunu ribbondan kaldırmış oluyoruz.</p>
<p style="text-align: justify;">Öncesi:</p>
<p style="text-align: justify;"><img class="aligncenter size-full wp-image-343" alt="sharepoint-ribbon-once" src="https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/09/sharepoint-ribbon-once.png" width="480" height="128" />Sonrası:</p>
<p style="text-align: justify;"><img class="aligncenter size-full wp-image-344" alt="sharepoint-ribbon-sonra" src="https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/09/sharepoint-ribbon-sonra.png" width="480" height="128" /><strong>B) Butonun Belirli Bir Liste veya Kütüphaneden Kaldırılması</strong></p>
<p style="text-align: justify;"><em>XML</em> dosyalarıyla belirli bir liste veya kütüphaneyi hedef alarak işlem yapmamız mümkün değil. Burada <em>Visual Studio 2010</em> kullanarak biraz kod yazmamız gerekiyor. Bunun için aşağıdaki adımları takip edebiliriz:</p>

<ol>
	<li style="text-align: justify;"><em>Visual Studio 2010</em>'da "<em>Empty Sharepoint Project</em>" seçiyoruz ve projemize sağ tıklayıp <em>Add</em> &gt; <em>New Item</em> yolunu izleyerek "<em>Empty Element</em>" ekliyoruz.</li>
	<li style="text-align: justify;">Özelliğimize (feature) sağ tıklayıp "Add Event Receiver" seçip aşağıdakine benzer bir kodu ekliyoruz.</li>
</ol>

<pre class="brush: c-sharp;">
public override void FeatureActivated(SPFeatureReceiverProperties properties)
{
  using(SPSite site = new SPSite("SiteURL"))
  using (SPWeb web = site.OpenWeb())
  {
    SPList list = web.Lists.TryGetList("ListeAdi");
    if (list != null)
    {
      var action = list.UserCustomActions.Add();
      action.Location = "CommandUI.Ribbon";
      action.Sequence = 50;
      action.Title = "Hide Button from Ribbon";
      action.CommandUIExtension = @"
      <CommandUIExtension><CommandUIDefinitions>
      <CommandUIDefinition Location=""Ribbon.List.CustomViews.CreateView"">
      </CommandUIDefinition>
      </CommandUIDefinitions>
      </CommandUIExtension>";
      action.Update();
    }
  }
}
</pre>

<p style="text-align: justify;">Projemizi deploy ettiğimiz zaman "ListeAdi" ile belirttiğimiz listemizdeki "Create View" butonunun gizlendiğini göreceksiniz. Tanımladığımız CustomAction'ı listemizden silmek içinse eklediğimiz EventReceiver'ın FeatureDeactivating metodunu aşağıdaki şekilde düzenlememiz gerekiyor:</p>
<pre class="brush: c-sharp;">
public override void FeatureDeactivating(SPFeatureReceiverProperties properties)
{
  using (SPSite site = new SPSite("SiteURL"))
  using (SPWeb web = site.OpenWeb())
  {
    SPList list = web.Lists.TryGetList("ListeAdi");
    if (list != null)
    {
      foreach (SPUserCustomAction action in list.UserCustomActions)
      {
        if (action.Title == "Hide Button from Ribbon")
        {
          action.Delete();
          break;
        }
      }
    }
  }
}
</pre>
