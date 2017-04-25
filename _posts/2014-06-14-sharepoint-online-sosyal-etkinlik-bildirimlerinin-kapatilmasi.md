---
layout: post
title: SharePoint Online Sosyal Etkinlik Bildirimlerinin Kapatılması
date: 2014-06-14 20:48
author: hasangok
comments: true
Tags: [SharePoint, Sharepoint 2013, SharePoint Online, Sosyal]
---
*SharePoint 2013 Online* ile geliştirdiğimiz bir sitede sosyal aktivitelerden alınacak e-posta bildirimlerinin bazı kullanıcılar için kapatılması istendi. CEO, Genel Müdür vb. konumdaki kullanıcılara ait hesaplar takip edildiğinde, bir gönderide etiketlendiğinde ve benzer durumlarda e-posta almamaları gerekiyordu.
Bu bildirimlerin varsayılan olarak tüm kullanıcılara kapatılması için bazı *PowerShell* scriptleri paylaşılmış olsa ne yazık ki bunları *Office 365* ortamında çalıştırma imkanım yoktu. Bu yüzden bu bildirimleri almasını istemediğimiz kullanıcılar için aşağıdaki adımları izledim:

1. *SharePoint yönetim merkezi*nden "*Kullanıcı Bilgileri*" sayfasına gidilir.
2. *Kullanıcı Profillerini Yönet* linkine tıklanır.
3. E-posta bildirimi almasını istemediğimiz kullanıcıyı arayıp, *Profili Düzenle* linkine tıklanır.
4. E-posta bildirimleri bölümündeki tüm seçenekler kaldırılır.

![sharepoint-email-notifications](https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2014/06/sharepoint-email-notifications.png "sharepoint-email-notifications")

*SharePoint*'in sosyal özelliklerine fazla aşina olmadığımdan bu yazıyı kendime not etmek istedim. Aynı ayarları kullanıcı isterse *Hakkımda* &gt; *Profili düzenle* &gt; *Haber Akışı Ayarları* yolunu izleyerek kendisi de yapabiliyor.
