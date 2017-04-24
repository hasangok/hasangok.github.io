---
layout: post
title: Media Web Part ile SharePoint Video Sitesi
date: 2013-08-29 15:51
author: hasangok
comments: true
Tags: [Asset Library, Media Web Part, Sharepoint, SharePoint, Varlık Kütüphanesi]
---
<p style="text-align: justify;">Varsayalım ki bir <em>SharePoint Asset Library</em> -Varlık Kütüphanesi- oluşturduk ve içerisine videolar yükledik. Bu kütüphanedeki videoların tamamını sayfamızda göstermek istiyoruz. Bunun için <em>SharePoint</em>'in <em>Media Web Part</em>'ını kullanacağız ve kütüphanemizdeki video sayımız kadar video oynatıcısını dinamik olarak sayfamızda oluşturacağız. Bunun için bir web part oluşturduk ve <strong>ASCX</strong> dosyasına "<em>videoPlayers</em>" adında bir literal kontrolü ekledik. Video oynatıcılarımızı oluşturmak için aşağıdakine benzer bir kodlama yapmamız gerekiyor.</p>
<p style="text-align: justify;">
<pre class="brush: c-sharp;">
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
</pre>
</p>
<p style="text-align: justify;">Burada <em><strong>&lt;object&gt;</strong></em> tagi ile media oynatıcıları oluşturmuş oluyoruz. <em>initParams</em> altında vermemiz gereken 3 önemli parametre var.</p>

<ol style="text-align: justify;">
	<li><strong>mediaTitle:</strong> Video player üzerinde görünecek olan başlık, ilgili kütüphanenin <em>BaseName</em> sütunundaki bilgi.</li>
	<li><strong>mediaSource:</strong> Video dosyamızın URL'i, ilgili kütüphanenin <em>EncodedAbsUrl</em> sütunundaki bilgi.</li>
	<li><strong>previewImageSource:</strong> Video player'ın göstereceği resim, ilgili kütüphanenin <em>AlternateThumbnailUrl</em> sütunundaki bilgi.</li>
</ol>
<p style="text-align: justify;">Basitçe, kütüphanedeki tüm videoları listelemek ve oynatabilmek için bu kadarı yeterli. Burada aklımıza hangi dosya türlerinin oynatılabildiğiyle alakalı bir soru gelebilir. <em>Media Web Part</em>'ı bir <em><strong>Silverlight</strong></em> kontrolü olduğu için <a href="http://msdn.microsoft.com/en-us/library/cc189080(VS.95).aspx" target="_blank">şu sayfada</a> belirtilen tüm biçimlerin desteklendiğini de söylemekte fayda var.</p>
<p style="text-align: justify;">İlgilenenler için <em>Media Web Part</em>'ın <em>JavaScript</em> kullanılarak nasıl oluşturulabildiğini <a title="SharePoint Media Web Part ile Video Oynatmak" href="http://www.hasangok.com.tr/109/sharepoint-media-web-part-ile-video-oynatmak.html">şu sayfa</a>da yazmıştım. Hatırlatmış olayım :)</p>
