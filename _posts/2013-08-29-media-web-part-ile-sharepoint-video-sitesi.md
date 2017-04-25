---
layout: post
title: Media Web Part ile SharePoint Video Sitesi
date: 2013-08-29 15:51
author: hasangok
comments: true
Tags: [Asset Library, Media Web Part, Sharepoint, SharePoint, Varlık Kütüphanesi]
---
Varsayalım ki bir *SharePoint Asset Library* -Varlık Kütüphanesi- oluşturduk ve içerisine videolar yükledik. Bu kütüphanedeki videoların tamamını sayfamızda göstermek istiyoruz. Bunun için *SharePoint*'in *Media Web Part*'ını kullanacağız ve kütüphanemizdeki video sayımız kadar video oynatıcısını dinamik olarak sayfamızda oluşturacağız. Bunun için bir web part oluşturduk ve **ASCX** dosyasına "*videoPlayers*" adında bir literal kontrolü ekledik. Video oynatıcılarımızı oluşturmak için aşağıdakine benzer bir kodlama yapmamız gerekiyor.

```csharp
SPList list = web.Lists.TryGetList("VideoLibrary");
foreach (SPListItem item in list.Items)
{
  videoPlayers.Text += string.Format(@"
   <object width="425" height="281" id="videoPlayer"
           data="data:application/x-oleobject;base64"
           type="application/x-silverlight">
      <param name="background" value="#80808080">
      <param name="enableHtmlAccess" value="true">
      <param name="source" value="/_layouts/clientbin/mediaplayer.xap">
      <param name="initParams" value="displayMode=Inline,mediaTitle={0},
          mediaSource={1},previewImageSource={2},
          loop=true,mediaFileExtensions=wmv;wma;avi;mpg;mp3;,
          silverlightMediaExtensions=wmv;wma;mp3;">
      <param name="windowless" value="true">
      <param name="onload" value="__slEvent0">
      <param name="onresize" value="__slEvent1">
   </object>", Convert.ToString(item["BaseName"]),
               Convert.ToString(item["EncodedAbsUrl"]),
               Convert.ToString(item["AlternateThumbnailUrl"]));
}
```

Burada ***&lt;object&gt;*** tagi ile media oynatıcıları oluşturmuş oluyoruz. *initParams* altında vermemiz gereken 3 önemli parametre var.

1. **mediaTitle:** Video player üzerinde görünecek olan başlık, ilgili kütüphanenin *BaseName* sütunundaki bilgi.
2. **mediaSource:** Video dosyamızın URL'i, ilgili kütüphanenin *EncodedAbsUrl* sütunundaki bilgi.
3. **previewImageSource:** Video player'ın göstereceği resim, ilgili kütüphanenin *AlternateThumbnailUrl* sütunundaki bilgi.

Basitçe, kütüphanedeki tüm videoları listelemek ve oynatabilmek için bu kadarı yeterli. Burada aklımıza hangi dosya türlerinin oynatılabildiğiyle alakalı bir soru gelebilir. *Media Web Part*'ı bir ***Silverlight*** kontrolü olduğu için [şu sayfada](http://msdn.microsoft.com/en-us/library/cc189080(VS.95).aspx) belirtilen tüm biçimlerin desteklendiğini de söylemekte fayda var.
İlgilenenler için *Media Web Part*'ın *JavaScript* kullanılarak nasıl oluşturulabildiğini <a title="SharePoint Media Web Part ile Video Oynatmak" href="http://www.hasangok.com.tr/109/sharepoint-media-web-part-ile-video-oynatmak.html">şu sayfa</a>da yazmıştım. Hatırlatmış olayım :)
