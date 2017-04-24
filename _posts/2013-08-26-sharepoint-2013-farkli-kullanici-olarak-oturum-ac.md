---
layout: post
title: SharePoint 2013 - Farklı Kullanıcı Olarak Oturum Aç
date: 2013-08-26 16:03
author: hasangok
comments: true
Tags: [Farklı Kullanıcı Olarak Oturum Aç, SharePoint, Sharepoint 2013, Sign in as Different User]
---
<p style="text-align: justify;"><em>SharePoint 2013</em>'te <em>Farklı Kullanıcı Olarak Oturum Aç</em> (<em>Sign in as a Different User</em>) özelliği kaldırılmış. Bunun yerine geri getirilmesi konusunda acı bir tecrübe yaşamışken buradan da paylaşmak istedim :)</p>
<p style="text-align: justify;">"<strong>C:\Program Files\Common Files\Microsoft Shared\Web Server Extensions\15\TEMPLATE\CONTROLTEMPLATES</strong>" klasörü altında bulunan "<em>Welcome.ascx</em>" dosyasını düzenleyip, "<em>ID_RequestAccess</em>" üzerine aşağıdaki ifadeyi ekliyoruz:</p>

<pre class="brush: javascript;">
<SharePoint:MenuItemTemplate runat="server" ID="ID_LoginAsDifferentUser" 
Text="<%$Resources:wss,personalactions_loginasdifferentuser%>" 
Description="<%$Resources:wss,personalactions_loginasdifferentuserdescription%>" 
MenuGroupId="100" Sequence="100" UseShortId="true" />
</pre>
