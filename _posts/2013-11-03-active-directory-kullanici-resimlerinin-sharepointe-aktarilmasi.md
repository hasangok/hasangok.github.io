---
layout: post
title: Active Directory Kullanıcı Resimlerinin SharePoint'e Aktarılması
date: 2013-11-03 13:14
author: hasangok
comments: true
Tags: [Active Directory, SharePoint, Sharepoint 2013, thumbnailPhoto, User Profile]
---
Daha önce yaşadığım bir problemi düzeltmek için yazdığım yazıda haberini vermiştim. Bu yazıda işin aslını, *Active Directory*'deki kullanıcı resimlerinin *SharePoint User Profile* ile nasıl senkronize edileceğini yazacağım.
İlk olarak yapmamız gereken *SharePoint Central Administration*'ı açıp *Application Management &gt; Manage Service Applications &gt; User Profile Service Application* yolunu izlemek. Buradan *People* başlığı altındaki *Manage User Properties* linkine tıklayıp, "***Picture***" isimli özelliği düzenliyoruz. Açılan sayfada "*Add New Mapping*" bölümünden *Active Directory* bağlantımızı seçiyor ve "*Attribute*" alanına "***thumbnailPhoto***" değerini seçiyoryuz. Bunu seçebileceğimiz bir alan yoksa elle de yazabiliriz. Daha sonra *Add* butonuna basıp *OK* diyerek değişikliğimizi kaydedip sayfadan ayrılıyoruz.

Yukarıda yazdığım aynı yolu izleyerek bu kez *Synchronization* başlığı altındaki "*Start Profile Synchronization*" linkine tıklıyor ve "***Start Full Synchronization***" seçiyoruz. Burada *Active Directory*'deki bilgiler *SharePoint User Profile*'a senkronize edilmiş oluyor.
Senkronizasyon da tamamlandıktan sonra *SharePoint Management Shell*'i açıp aşağıdaki kodu çalıştırıyoruz:

```powershell
Update-SPProfilePhotoStore -CreateThumbnailsForImportedPhotos 1 -MySiteHostLocation http://MySiteURL
```
Burada dikkat edilmesi gereken nokta, yine yukarıdaki aynı yolu izleyerek *My Site Settings* başlığı altından *Setup My Sites* linkine tıklayıp, bu sayfadaki "***My Site Host Location***" alanında yazan değeri yukarıdaki kodda ilgili yere doğru bir şekilde yazmak. Yoksa çözümünü <a title="SharePoint User Profile’daki Hatalı Profil Resmi URL’lerin Düzeltilmesi" href="http://www.hasangok.com.tr/424/sharepoint-user-profiledaki-hatali-profil-resmi-urllerin-duzeltilmesi.html">burada</a> belirttiğim şekilde hata düzeltmek zorunda kalabilirsiniz.
Bu işlemlerden sonra kullanıcı resimleriniz profillerine senkronize edilmiş olacak. *SharePoint* kişi arama sayfasında da bu resimlerin görünebilmesi için *Search Service Application*'da *Full Crawl* yapmanız gerektiğini de söyleyerek yazımı bitireyim.
Başka bir konuyla başka bir yazıda görüşünceye dek, esen kalın...
