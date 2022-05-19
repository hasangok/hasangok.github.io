---
title: SharePoint 2013 - Farklı Kullanıcı Olarak Oturum Aç
date: 2013-08-26 16:03
---

*SharePoint 2013*'te *Farklı Kullanıcı Olarak Oturum Aç* (*Sign in as a Different User*) özelliği kaldırılmış. Bunun yerine geri getirilmesi konusunda acı bir tecrübe yaşamışken buradan da paylaşmak istedim 🙂

<!--more-->
"**C:\Program Files\Common Files\Microsoft Shared\Web Server Extensions\15\TEMPLATE\CONTROLTEMPLATES**" klasörü altında bulunan "*Welcome.ascx*" dosyasını düzenleyip, "*ID_RequestAccess*" üzerine aşağıdaki ifadeyi ekliyoruz:

```xml
<SharePoint:MenuItemTemplate
    runat="server" ID="ID_LoginAsDifferentUser"
    Text="<%$Resources:wss,personalactions_loginasdifferentuser%>"
    Description="<%$Resources:wss,personalactions_loginasdifferentuserdescription%>"
    MenuGroupId="100"
    Sequence="100"
    UseShortId="true" />
```
