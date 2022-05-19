---
title: Kullanıcının SharePoint Grubu İçinde Olması
date: 2013-08-28 15:59
---

Geliştirdiğimiz web partların *farklı kullanıcı gruplarına farklı görünmesi*ni isteyebiliyoruz. Bunun için oturum açmış kullanıcının ilgili gruplar içerisinde olup olmadığını aşağıdaki şekilde kontrol edebiliriz:

<!--more-->
```csharp
SPWeb web = SPContext.Current.Web;
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
}
```
Burada *RunWithElevatedPrivileges* (ne olduğunu [burada](/2013/08/19/web-partta-full-control-yetkisi.html) yazmıştım) metodunu kullanmamızın sebebi, eğer kullanıcımızın diğer grupları görme yetkisi yoksa sayfada hata mesajı görmeden ilgili kontrolü sorunsuzca yapabilmemizi sağlamak.
