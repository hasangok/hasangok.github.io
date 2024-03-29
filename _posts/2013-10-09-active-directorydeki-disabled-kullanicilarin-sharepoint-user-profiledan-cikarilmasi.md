---
title: Active Directory'deki Disabled Kullanıcıların SharePoint User Profile'dan Çıkarılması
date: 2013-10-09 12:15
---

Yaşadığım son problem buydu. İşten çıktığı için *Active Directory*'den pasif edilmiş (*disabled*) kullanıcıların, *SharePoint User Profile* içerisinde halen yer alması ve arama sonuçlarında bu kişilerin görülmesi. İstenmeyen bu durumdan kurtulmak için şu adımları izlememiz gerekiyor:

<!--more-->
* *SharePoint Central Administration*'ı açıp "*Manage Service Applications*" linkine tıklıyoruz.
* *User Profile Service Application* seçip, "*Synchronization*" bölümü altında bulunan "*Configure Synchronization Connections*" linkine tıklıyoruz.

![user-profile-service-app-1](/uploads/2013/10/user-profile-service-app-1.png)

* Buradan *Active Directory*'e bağlantımızı sağlayan kayda tıklayıp "*Edit Connection Filters*" diyoruz.

![user-profile-service-app-2](/uploads/2013/10/user-profile-service-app-2.png)

* "Exclusion Filter for Users" bölümü altında şu seçimleri yapıyoruz:

**Attribute:** userAccountControl

**Operator:** Bit on equals

**Filter:** 2

![user-profile-service-app-3](/uploads/2013/10/user-profile-service-app-3.png)

* *Add* tuşuna basıyor ve *OK* deyip değişikliklerimizi uyguluyoruz.

Gerekli filtreleme işlemini burada tamamlamış olduk. Bundan sonra *User Profile Service Application*'da "**Full Synchronization**", *Search Service Application*'da "**Full Crawl**" işlemlerini yaparsak disable edilmiş kullanıcıları artık arama sonuçlarında ve *User Profile*'da görmeyeceğiz.
