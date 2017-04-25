---
layout: post
title: SharePoint Online Sosyal Etkinlik Bildirimlerinin Kapatılması
date: 2014-06-14 20:48
author: hasangok
comments: true
Tags: [SharePoint, Sharepoint 2013, SharePoint Online, Sosyal]
---
<p style="text-align: justify;"><em>SharePoint 2013 Online</em> ile geliştirdiğimiz bir sitede sosyal aktivitelerden alınacak e-posta bildirimlerinin bazı kullanıcılar için kapatılması istendi. CEO, Genel Müdür vb. konumdaki kullanıcılara ait hesaplar takip edildiğinde, bir gönderide etiketlendiğinde ve benzer durumlarda e-posta almamaları gerekiyordu.</p>
<p style="text-align: justify;">Bu bildirimlerin varsayılan olarak tüm kullanıcılara kapatılması için bazı <em>PowerShell</em> scriptleri paylaşılmış olsa ne yazık ki bunları <em>Office 365</em> ortamında çalıştırma imkanım yoktu. Bu yüzden bu bildirimleri almasını istemediğimiz kullanıcılar için aşağıdaki adımları izledim:</p>

<ol style="text-align: justify;">
	<li><em>SharePoint yönetim merkezi</em>nden "<em>Kullanıcı Bilgileri</em>" sayfasına gidilir.</li>
	<li><em>Kullanıcı Profillerini Yönet</em> linkine tıklanır.</li>
	<li>E-posta bildirimi almasını istemediğimiz kullanıcıyı arayıp, <em>Profili Düzenle</em> linkine tıklanır.</li>
	<li>E-posta bildirimleri bölümündeki tüm seçenekler kaldırılır.</li>
</ol>
<p style="text-align: justify;"><img class="aligncenter size-full wp-image-708" src="https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2014/06/sharepoint-email-notifications.png" alt="sharepoint-email-notifications" width="528" height="173" /></p>
<p style="text-align: justify;"><em>SharePoint</em>'in sosyal özelliklerine fazla aşina olmadığımdan bu yazıyı kendime not etmek istedim. Aynı ayarları kullanıcı isterse <em>Hakkımda</em> &gt; <em>Profili düzenle</em> &gt; <em>Haber Akışı Ayarları</em> yolunu izleyerek kendisi de yapabiliyor.</p>
