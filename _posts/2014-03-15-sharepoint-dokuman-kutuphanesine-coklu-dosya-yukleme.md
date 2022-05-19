---
title: SharePoint Doküman Kütüphanesine Çoklu Dosya Yükleme
date: 2014-03-15 12:45
---

Son birkaç günümü bu konu üzerinde araştırmalarla geçirdim. İlk başta *FileUpload* kontrolü ile bu isteği gerçekleştirmiş olsam da daha kolay, daha hızlı ve daha sorunsuz bir yöntem olmasından dolayı **UploadCtl** adlı *ActiveX* bişelenini kullanmaya karar verdim. Oluşturduğunuz bir *Visual Web Part*'ın *ASCX* dosyasına aşağıdaki kodları eklemeniz, belirttiğiniz kütüphaneye dosya yüklemenize olanak sağlıyor:

<!--more-->
```html
<script type="text/jscript">
    function DocumentUpload() {
        var uploadCtl = document.getElementById("idUploadCtl");
        uploadCtl.MultipleUpload();
    }
</script>

<input type="hidden" name="Cmd" value="Save" />
<input type="hidden" name="putopts" value="true" />
<input type="hidden" name="Confirmation-URL" value="web/url/lists/listname" />
<input type="hidden" name="PostURL" value="" />
<input type="hidden" name="VTI-GROUP" value="0" />
<input type="hidden" name="destination" id="destination" value="/web/url/lists/listname">

<asp:Panel runat="server" Width="100%">
    <script>
        try {
            if (new ActiveXObject("STSUpld.UploadCtl"))
                document.write("<OBJECT id=\"idUploadCtl\" name=\"idUploadCtl\" CLASSID=\"CLSID:07B06095-5687-4d13-9E32-12B4259C9813\" WIDTH=\"100%\" HEIGHT=\"350px\"></OBJECT>");
        }
        catch (error) {
        }
    </script>
    <asp:Button runat="server" accesskey="O" id="btnTamam" CssClass="ms-ButtonHeightWidth" Text="Dosyaları Yükle" UseSubmitBehavior="False" OnClientClick="DocumentUpload(); return false;"/>
    <asp:Button runat="server" accesskey="C" id="btnIptal" CssClass="ms-ButtonHeightWidth" Text="İptal" UseSubmitBehavior="False" style="display: none;"/>
</asp:Panel>
```
Yukarıda gördüğünüz gizlenmiş input'lar kontrolümüzün nasıl çalışacağını ayarlamış oluyoruz. ***putopts*** ile varolan dosyaların üzerine yazıp yazmayacağımızı, ***destionation*** ile yükleme yapacağımız doküman kütüphanesi veya klasörün yolunu belirleyebiliriz. Tarayıcımızda *ActiveX*'in devre dışı olmaması gerektiğini de unutmayın.

İyi çalışmalar...
