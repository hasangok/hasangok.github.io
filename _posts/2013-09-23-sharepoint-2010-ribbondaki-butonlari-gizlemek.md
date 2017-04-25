---
layout: post
title: SharePoint 2010 - Ribbon'daki Butonları Gizlemek
date: 2013-09-23 16:29
author: hasangok
comments: true
Tags: [Buton Gizlemek, Ribbon, Sharepoint, SharePoint]
---
![SharePoint2010](https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/09/SharePoint2010.jpg)
*SharePoint 2010*'da herhangi bir liste ya da kütüphanenin ribbon menüsündeki çeşitli butonları gizlemeye ihtiyacımız olabiliyor. Son çalışmam, belirli bir listedeki "**Create View**" (*Görünüm Oluştur*), ve "**Modify View**" (*Görünümü Özelleştir*) butonlarının Ribbon'dan kaldırılması yönündeydi. Bunun için bir "**feature**" (özellik) hazırlamam istendi, böylece bu fonksiyon "**Manage Site Feeatures**" (*Site Özelliklerini Yönet*) altından aktif/pasif durumuna geçebilecekti. Ben bu yazımda hem sitemizdeki tüm listeler/kütüphaneler için geçerli olacak ve sadece *XML* dosyalarıyla hazırlanabilecek bir özellik oluşturmayı, hem de *Visual Studio 2010* kullanarak sadece istediğimiz listelerde geçerli olacak bir özellik oluşturmayı anlatmaya çalışacağım.
**A) Butonun Tüm Liste veya Kütüphanelerden Kaldırılması**
2 adet *XML* dosyası ile oluşturabileceğimiz bu özellik için şu dizinde yeni bir klasör oluşturmamız gerekiyor: "*C:\Program Files\Common Files\Microsoft Shared\Web Server Extensions\14\TEMPLATE\FEATURES*". Yazıma, klasör adını "**DisableRibbonButton**" olarak belirlediğiniz varsayımıyla devam edeceğim. Şimdi *DisableRibbonButton* klasörü içinde "***feature.xml***" adlı bir dosya oluşturup içeriğini aşağıdakiyle değiştiriyoruz:

```xml
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
```

Ardından "***Manifest.xml***" adlı başka bir dosya oluşturup içeriğini aşağıdakiyle değiştiriyoruz:

```xml
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
```

*Manifest.xml* dosyasında önemli iki nokta var. Bunlardan ilki **RegistrationId** kısmı. Burada özelliğimiz nerede çalışacak onu belirliyoruz. Benim kullanıdığım 100 özel listeleri belirtirken, 101 Döküman Kütüphanesini belirtiyor. Diğer liste ve kütüphaneler için detaylı bilgiye [bu sayfa](http://msdn.microsoft.com/en-us/library/microsoft.sharepoint.splisttemplatetype.aspx)dan ulaşabilirsiniz. İkinci önemli kısmı ise *CommandUIDefinition* altındaki **Location** değeri. Burada hangi butonun gizleneceğini belirtmiş oluyoruz ki her bir buton için Location değerlerini bulabileceğiniz listeye [buraya](http://msdn.microsoft.com/en-us/library/ee537543.aspx) tıklayarak ulaşabilirsiniz.
Bu iki dosyayı belirtilen yolda oluşturduğumuz klasör altında oluşturduğumuza göre özelliğimiz hazır demektir. Şimdi bunu sitemize yükleyip aktifleştirmemiz gerekiyor.
```powershell
Install-SPFeature DisableRibbonButton
Enable-SPFeature DisableRibbonButton –url http://&lt;server_adresi&gt;*
```
Tüm bu işlemlerden sonra "**Create View**" butonunu ribbondan kaldırmış oluyoruz.
Öncesi:
![sharepoint-ribbon-once](https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/09/sharepoint-ribbon-once.png)
Sonrası:
![sharepoint-ribbon-sonra](https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/09/sharepoint-ribbon-sonra.png)

**B) Butonun Belirli Bir Liste veya Kütüphaneden Kaldırılması**
*XML* dosyalarıyla belirli bir liste veya kütüphaneyi hedef alarak işlem yapmamız mümkün değil. Burada *Visual Studio 2010* kullanarak biraz kod yazmamız gerekiyor. Bunun için aşağıdaki adımları takip edebiliriz:

1. *Visual Studio 2010*'da "*Empty Sharepoint Project*" seçiyoruz ve projemize sağ tıklayıp *Add* &gt; *New Item* yolunu izleyerek "*Empty Element*" ekliyoruz.
2. Özelliğimize (feature) sağ tıklayıp "Add Event Receiver" seçip aşağıdakine benzer bir kodu ekliyoruz.

```csharp
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
```

Projemizi deploy ettiğimiz zaman "ListeAdi" ile belirttiğimiz listemizdeki "Create View" butonunun gizlendiğini göreceksiniz. Tanımladığımız CustomAction'ı listemizden silmek içinse eklediğimiz EventReceiver'ın FeatureDeactivating metodunu aşağıdaki şekilde düzenlememiz gerekiyor:

```csharp
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
```
