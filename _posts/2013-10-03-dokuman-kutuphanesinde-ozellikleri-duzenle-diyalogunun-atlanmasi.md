---
title: Döküman Kütüphanesinde Özellikleri Düzenle Diyalogunun Atlanması
date: 2013-10-03 17:01
---

*SharePoint 2013*'te, bir döküman kütüphanesine dosya yüklenmesi sonrası açılan "**Özellikleri Düzenle**" (*Edit Properties*) diyalogunun atlanmasına ihtiyacım vardı. Bunu yapacak JavaScript kodları şu şekilde:

<!--more-->
```javascript
  _spBodyOnLoadFunctionNames.push("Redirect");
  function Redirect()
  {
     var mode = getURLParam('Mode');
     if (mode == "Upload")
       window.frameElement.commonModalDialogClose(1, 'saved');
  }
  function getURLParam(name)
  {
     name = name.replace(/[\[]/,"\\\[").replace(/[\]]/,"\\\]");
     var regexS = "[\\?&amp;]"+name+"=([^&amp;#]*)";
     var regex = new RegExp( regexS );
     var results = regex.exec( window.location.href );
     if(results == null)
       return "";
     else
       return results[1];
  }
  function replaceCharacters(str)
  {
     str = str.replace(/%20/g, " ");
     str = str.replace(/%2F/g, "/");
     str = str.replace(/%3A/g, ":");
     str = str.replace(/%2E/g, ".");
     return str;
  }
```

Bunu ilgili yere eklemenin iki yolu var. Birincisi, "*Özellikleri Düzenle*" penceresi açıkken adres çubunun sonuna "**&amp;ToolPaneView=2**" ekleyip, sayfamıza bir "*İçerik Düzenleyicisi*" (*Content Editor*) web partı ekleyerek yukarıdaki kodu HTML içeriğine eklemek. İkinci yol için *SharePoint Designer* kullanarak sitemize bağlanmamız gerekiyor. Aşağıdaki resimde de gördüğünüz üzere sol tarafta bulunan "*List and Libraries*" bölümünden ilgili kütüphanemizi seçip, **EditForm.aspx** dosyamıza sağ tıklayıp bu dosyayı düzenlememiz gerekiyor. Aşağıdaki satırı bulup hemen altına yukarıdaki kodları ekleyip dosyamızı kaydedersek, açılan bu pencereyi savuşturmuş oluyoruz.

```html
<asp:Content ContentPlaceHolderId="PlaceHolderMain" runat="server">
```

![sharepoint-designer](/uploads/2013/10/sharepoint-designer.png)

Ben bu yöntemi *SharePoint 2013* için kullandım ve başarılı oldum. Aynısı *SharePoint 2010* için de kullanılabilir.