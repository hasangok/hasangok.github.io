---
layout: post
title: Active Directory'deki Disabled Kullanıcıların SharePoint User Profile'dan Çıkarılması
date: 2013-10-09 12:15
author: hasangok
comments: true
Tags: [Active Directory, Disabled Users, Search Service, Sharepoint, SharePoint, User Profile]
---
<p style="text-align: justify;">Yaşadığım son problem buydu. İşten çıktığı için <em>Active Directory</em>'den pasif edilmiş (<em>disabled</em>) kullanıcıların, <em>SharePoint User Profile</em> içerisinde halen yer alması ve arama sonuçlarında bu kişilerin görülmesi. İstenmeyen bu durumdan kurtulmak için şu adımları izlememiz gerekiyor:</p>

<ol style="text-align: justify;">
	<li><em>SharePoint Central Administration</em>'ı açıp "<em>Manage Service Applications</em>" linkine tıklıyoruz.</li>
	<li><em>User Profile Service Application</em> seçip, "<em>Synchronization</em>" bölümü altında bulunan "<em>Configure Synchronization Connections</em>" linkine tıklıyoruz.
<img class="aligncenter size-full wp-image-394" alt="user-profile-service-app-1" src="https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/10/user-profile-service-app-1.png" width="778" height="453" /></li>
	<li>Buradan <em>Active Directory</em>'e bağlantımızı sağlayan kayda tıklayıp "<em>Edit Connection Filters</em>" diyoruz.
<img class="aligncenter size-full wp-image-395" alt="user-profile-service-app-2" src="https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/10/user-profile-service-app-2.png" width="778" height="453" /></li>
	<li>"Exclusion Filter for Users" bölümü altında şu seçimleri yapıyoruz:
<strong>Attribute:</strong> userAccountControl
<strong>Operator:</strong> Bit on equals
<strong>Filter:</strong> 2
<img class="aligncenter size-full wp-image-396" alt="user-profile-service-app-3" src="https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/10/user-profile-service-app-3.png" width="778" height="470" /></li>
	<li><em>Add</em> tuşuna basıyor ve <em>OK</em> deyip değişikliklerimizi uyguluyoruz.</li>
</ol>
<p style="text-align: justify;">Gerekli filtreleme işlemini burada tamamlamış olduk. Bundan sonra <em>User Profile Service Application</em>'da "<strong>Full Synchronization</strong>", <em>Search Service Application</em>'da "<strong>Full Crawl</strong>" işlemlerini yaparsak disable edilmiş kullanıcıları artık arama sonuçlarında ve <em>User Profile</em>'da görmeyeceğiz.</p>
