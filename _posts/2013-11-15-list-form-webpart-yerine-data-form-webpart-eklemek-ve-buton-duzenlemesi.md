---
title: List Form WebPart Yerine Data Form WebPart Eklemek ve Buton Düzenlemesi
date: 2013-11-15 09:23
---

**SharePoint 2010** kullananların en çok gördüğü pencerelerden biridir sanırım aşağıdaki pencere (en azından benim için öyle). Evet, doğru tahmin ettiniz. Bu pencereyle alakalı bir sorun yaşayıp yeni bir şey öğrendiğim için, bunu sizlerle de paylaşıyorum 😉

<!--more-->
![sharepoint-2010-add-new-item](/uploads/2013/11/sharepoint-2010-add-new-item.png)

Varsayalım ki listemize yeni bir kayıt giriyoruz, ekranımızda yukarıda gördüğünüz pencere varken tarayıcımızın adres çubuğunda şu URL görünüyor:

```
http://sharepointURL/Lists/Test/NewForm.aspx?Source=/Pages/Kaydedildi.aspx
```

Biliyoruz ki kaydımızı girmek için *Kaydet* (**Save**) butonuna bassak da, vazgeçip *İptal* (**Cancel**) butonuna bassak da, URL'de **Source** parametresiyle belirtilen "*/Pages/Kaydedildi.aspx*" sayfasına yönlendirileceğiz. Peki, *Kaydet* butonuna basınca bu sayfaya gidip *İptal* butonuna basınca başka bir sayfaya gitmek istiyorsak ne yapacağız? Bu soruya verdiğim ilk cevap bir *JavaScript* kodu yazıp *İptal* butonuna tıklandığında istediğimiz sayfaya yönlendirmek şeklinde oldu. Hatta şu şekilde hemen bu isteği gerçekleştirebildim:

```javascript
$(document).ready(function() {
  if(window.location.href.indexOf("AnketURL") !=-1){
    var allElements = document.getElementsByTagName('*');
    for (var i = 0; i &lt; allElements.length; i++) {
      if(String(allElements[i].getAttribute('id')).indexOf("diidIOGoBack") !=-1){
         allElements[i].attachEvent('onclick',redirect,false);
      }
    }
  }

  function redirect(){
       window.location.href = "/Pages/IptalEdildi.aspx";
  }
});
```
Bu tabi ki bir çözümdü. Ancak *JavaScript* kodlarının client bazında farklı davranabiliyor olması yüzünden, liste üzerindeki ekleme, düzenleme vb. işlemlerde *JavaScript* ile değil, *XSL* ile değişiklikler yapmanın doğru ve uygun bir yöntem olduğunu öğrendim. Hal böyle olunca yapılması gereken, listemizin **NewForm.aspx** dosyasında düzenleme yapmak oldu. Bunun için aşağıdaki adımları takip edebilirsiniz:

1. *SharePoint Designer 2010* ile sitemize bağlanıp ilgili listeyi bulduktan sonra, *NewForm.aspx* dosyasına sağ tıklayıp "**Edit File in Advanced Mode**" seçeneğine tıklıyoruz.
![newform.aspx](/uploads/2013/11/newform.aspx_.png)
2. Tasarım (Design) moduna geçip List Form Web Part'ın önizlemesine tıklayarak tekrar kodlara döndüğümüzde seçili olan kod bloğunu siliyoruz.
![sharepoint-designer-listformwebpart](/uploads/2013/11/sharepoint-designer-listformwebpart.png)
3. Sildiğimiz yerde kalmak şartıyla (aynı zone içerisinde) *Ribbon*'daki **Insert** menüsünden **New Item Form** butonuna tıklayıp **Custom List Form** seçeneğine tıklıyoruz.
![sharepoint-designer-custom-list-form](/uploads/2013/11/sharepoint-designer-custom-list-form.png)
4. Gelen pencerede ilgili listemizi ve *New Item Form*'u seçerek **OK** diyoruz.

Bu aşamada *List Form Web Part*'ı sayfamızdan silip yerine *Data Form Web Part* eklemiş oluyoruz. Artık butonlarla uğraşabiliriz.

![sharepoint-designer-data-form-web-part](/uploads/2013/11/sharepoint-designer-data-form-web-part.png)

Tasarım moduna geçip yeni eklenen web partı incelersek, *List Form Web Part*'ın aksine sayfa içerisindeki elemanlara ulaşıp bunları düzenleyebildiğimizi göreceğiz. Konumuz olan *İptal* (**Cancel**) butonlarına geri dönelim. Kodumuzda aşağıdaki iki satırı bulalım:

```html
<SharePoint:GoBackButton runat="server" ControlMode="New" id="gobackbutton1"/>
<SharePoint:GoBackButton runat="server" ControlMode="New" id="gobackbutton2"/>
```
Bu iki satırı aşağıdaki kod ile değiştirelim:

```html
<input type="button" class="ms-ButtonHeightWidth" value="İptal" name="btnCancel" onclick="javascript: {ddwrt:GenFireServerEvent('__redirect={/Pages/IptalEdildi.aspx}')}" />
```
Bu değişikliği yaptıktan sonra dosyamızı kaydedersek göreceğiz ki *Kaydet* (**Save**) butonu bizi URL'deki *Source* ile belirtilen "*/Pages/Kaydedildi.aspx*" adresine yönlendirirken, *İptal* (**Cancel**) butonu **GenFireServerEvent** içerisinde belirttiğimiz "*/Pages/IptalEdildi.aspx*" sayfasına yönlendirecek.
