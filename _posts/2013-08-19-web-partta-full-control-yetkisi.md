---
layout: post
title: Web Partta Full Control Yetkisi
date: 2013-08-19 15:19
author: hasangok
comments: true
Tags: [RunWithElevatedPrivileges, Sharepoint, SharePoint, Web Part]
---
<p style="text-align: justify;">Yazdığımız web partlarda bazı kodların tam denetim yetkisiyle çalışmasını isteyebiliyoruz. Benim için bu ihtiyaç <em>User Profile</em>'dan bilgi çekip, kişilerin doğum günlerini göstermek istediğimde ortaya çıkmıştı. <strong>Full Control</strong> -<em>Tam Denetim</em>- yetkisiyle çalıştırmak istediğimiz kod kısımlarını aşağıdaki metod içerisine yazarsak işimiz görülmüş oluyor:</p>
<p style="text-align: justify;">
<pre class="brush: c-sharp;">
SPSecurity.RunWithElevatedPrivileges(delegate()
{
	//Tam denetim yetkisi ile
	//çalışacak kodlar
});
</pre>
</p>
<p style="text-align: justify;"><strong>Not:</strong> Sandbox projelerde "<strong><em>RunWithElevatedPrivileges</em></strong>" metodunun kullanılamayacağını da belirteyim.</p>
