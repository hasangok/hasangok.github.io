---
layout: post
title: Active Directory Kullanıcı Resimlerinin SharePoint'e Aktarılması
date: 2013-11-03 13:14
author: hasangok
comments: true
Tags: [Active Directory, SharePoint, Sharepoint 2013, thumbnailPhoto, User Profile]
---
<p style="text-align: justify;">Daha önce yaşadığım bir problemi düzeltmek için yazdığım yazıda haberini vermiştim. Bu yazıda işin aslını, <em>Active Directory</em>'deki kullanıcı resimlerinin <em>SharePoint User Profile</em> ile nasıl senkronize edileceğini yazacağım.</p>
<p style="text-align: justify;">İlk olarak yapmamız gereken <em>SharePoint Central Administration</em>'ı açıp <em>Application Management &gt; Manage Service Applications &gt; User Profile Service Application</em> yolunu izlemek. Buradan <em>People</em> başlığı altındaki <em>Manage User Properties</em> linkine tıklayıp, "<strong><em>Picture</em></strong>" isimli özelliği düzenliyoruz. Açılan sayfada "<em>Add New Mapping</em>" bölümünden <em>Active Directory</em> bağlantımızı seçiyor ve "<em>Attribute</em>" alanına "<strong><em>thumbnailPhoto</em></strong>" değerini seçiyoryuz. Bunu seçebileceğimiz bir alan yoksa elle de yazabiliriz. Daha sonra <em>Add</em> butonuna basıp <em>OK</em> diyerek değişikliğimizi kaydedip sayfadan ayrılıyoruz.</p>
<!--more-->
<p style="text-align: justify;">Yukarıda yazdığım aynı yolu izleyerek bu kez <em>Synchronization</em> başlığı altındaki "<em>Start Profile Synchronization</em>" linkine tıklıyor ve "<strong><em>Start Full Synchronization</em></strong>" seçiyoruz. Burada <em>Active Directory</em>'deki bilgiler <em>SharePoint User Profile</em>'a senkronize edilmiş oluyor.</p>
<p style="text-align: justify;">Senkronizasyon da tamamlandıktan sonra <em>SharePoint Management Shell</em>'i açıp aşağıdaki kodu çalıştırıyoruz:</p>

<pre class="lang:default decode:true">Update-SPProfilePhotoStore -CreateThumbnailsForImportedPhotos 1 -MySiteHostLocation http://MySiteURL</pre>
<p style="text-align: justify;">Burada dikkat edilmesi gereken nokta, yine yukarıdaki aynı yolu izleyerek <em>My Site Settings</em> başlığı altından <em>Setup My Sites</em> linkine tıklayıp, bu sayfadaki "<strong><em>My Site Host Location</em></strong>" alanında yazan değeri yukarıdaki kodda ilgili yere doğru bir şekilde yazmak. Yoksa çözümünü <a title="SharePoint User Profile’daki Hatalı Profil Resmi URL’lerin Düzeltilmesi" href="http://www.hasangok.com.tr/424/sharepoint-user-profiledaki-hatali-profil-resmi-urllerin-duzeltilmesi.html">burada</a> belirttiğim şekilde hata düzeltmek zorunda kalabilirsiniz.</p>
<p style="text-align: justify;">Bu işlemlerden sonra kullanıcı resimleriniz profillerine senkronize edilmiş olacak. <em>SharePoint</em> kişi arama sayfasında da bu resimlerin görünebilmesi için <em>Search Service Application</em>'da <em>Full Crawl</em> yapmanız gerektiğini de söyleyerek yazımı bitireyim.</p>
<p style="text-align: justify;">Başka bir konuyla başka bir yazıda görüşünceye dek, esen kalın...</p>
