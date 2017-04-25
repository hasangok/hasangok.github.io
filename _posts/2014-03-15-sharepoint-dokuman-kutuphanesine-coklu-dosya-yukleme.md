---
layout: post
title: SharePoint Doküman Kütüphanesine Çoklu Dosya Yükleme
date: 2014-03-15 12:45
author: hasangok
comments: true
Tags: [Çoklu dosya yükleme, Döküman Kütüphanesi, JavaScript, Sharepoint, SharePoint, UploadCtl]
---
Son birkaç günümü bu konu üzerinde araştırmalarla geçirdim. İlk başta *FileUpload* kontrolü ile bu isteği gerçekleştirmiş olsam da daha kolay, daha hızlı ve daha sorunsuz bir yöntem olmasından dolayı **UploadCtl** adlı *ActiveX* bişelenini kullanmaya karar verdim. Oluşturduğunuz bir *Visual Web Part*'ın *ASCX* dosyasına aşağıdaki kodları eklemeniz, belirttiğiniz kütüphaneye dosya yüklemenize olanak sağlıyor:

```html
&lt;script type="text/jscript"&gt;
    function DocumentUpload() {
        var uploadCtl = document.getElementById("idUploadCtl");
        uploadCtl.MultipleUpload();
    }
&lt;/script&gt;

&lt;input type="hidden" name="Cmd" value="Save" /&gt;
&lt;input type="hidden" name="putopts" value="true" /&gt;
&lt;input type="hidden" name="Confirmation-URL" value="web/url/lists/listname" /&gt;
&lt;input type="hidden" name="PostURL" value="" /&gt;
&lt;input type="hidden" name="VTI-GROUP" value="0" /&gt;
&lt;input type="hidden" name="destination" id="destination" value="/web/url/lists/listname"&gt;

&lt;asp:Panel runat="server" Width="100%"&gt;
    &lt;script&gt;
        try {
            if (new ActiveXObject("STSUpld.UploadCtl"))
                document.write("&lt;OBJECT id=\"idUploadCtl\" name=\"idUploadCtl\" CLASSID=\"CLSID:07B06095-5687-4d13-9E32-12B4259C9813\" WIDTH=\"100%\" HEIGHT=\"350px\"&gt;&lt;/OBJECT&gt;");
        }
        catch (error) {
        }
    &lt;/script&gt;
    &lt;asp:Button runat="server" accesskey="O" id="btnTamam" CssClass="ms-ButtonHeightWidth" Text="Dosyaları Yükle" UseSubmitBehavior="False" OnClientClick="DocumentUpload(); return false;"/&gt;
    &lt;asp:Button runat="server" accesskey="C" id="btnIptal" CssClass="ms-ButtonHeightWidth" Text="İptal" UseSubmitBehavior="False" style="display: none;"/&gt;
&lt;/asp:Panel&gt;
```
Yukarıda gördüğünüz gizlenmiş input'lar kontrolümüzün nasıl çalışacağını ayarlamış oluyoruz. ***putopts*** ile varolan dosyaların üzerine yazıp yazmayacağımızı, ***destionation*** ile yükleme yapacağımız doküman kütüphanesi veya klasörün yolunu belirleyebiliriz. Tarayıcımızda *ActiveX*'in devre dışı olmaması gerektiğini de unutmayın.
İyi çalışmalar...
