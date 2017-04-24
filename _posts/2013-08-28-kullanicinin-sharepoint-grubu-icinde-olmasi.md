---
layout: post
title: Kullanıcının SharePoint Grubu İçinde Olması
date: 2013-08-28 15:59
author: hasangok
comments: true
Tags: [IsCurrentUserMemberOfGroup, Kullanıcı Grubu, Sharepoint, SharePoint]
---
<p style="text-align: justify;">Geliştirdiğimiz web partların <em>farklı kullanıcı gruplarına farklı görünmesi</em>ni isteyebiliyoruz. Bunun için oturum açmış kullanıcının ilgili gruplar içerisinde olup olmadığını aşağıdaki şekilde kontrol edebiliriz:</p>

<pre class="brush: c-sharp;">SPWeb web = SPContext.Current.Web;
bool result = false;
SPSecurity.RunWithElevatedPrivileges(delegate()
{
  result = web.IsCurrentUserMemberOfGroup(web.Groups["GrupAdi"].ID);
});
if (result == true)
{
  //grup içindeyse çalışacak kodlar
}
else
{
  //grupta değilse çalışacak kodlar
}</pre>
<p style="text-align: justify;">Burada <em>RunWithElevatedPrivileges</em> (ne olduğunu <a title="Web Partta Full Control Yetkisi" href="http://www.hasangok.com.tr/226/web-partta-full-control-yetkisi.html">burada</a> yazmıştım) metodunu kullanmamızın sebebi, eğer kullanıcımızın diğer grupları görme yetkisi yoksa sayfada hata mesajı görmeden ilgili kontrolü sorunsuzca yapabilmemizi sağlamak.</p>
