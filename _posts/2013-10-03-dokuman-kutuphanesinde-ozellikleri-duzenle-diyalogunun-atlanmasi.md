---
layout: post
title: Döküman Kütüphanesinde Özellikleri Düzenle Diyalogunun Atlanması
date: 2013-10-03 17:01
author: hasangok
comments: true
Tags: [Döküman Kütüphanesi, JavaScript, Özellikleri Düzenle, Sharepoint, SharePoint, SharePoint Designer]
---
<p style="text-align: justify;"><em>SharePoint 2013</em>'te, bir döküman kütüphanesine dosya yüklenmesi sonrası açılan "<strong>Özellikleri Düzenle</strong>" (<em>Edit Properties</em>) diyalogunun atlanmasına ihtiyacım vardı. Bunu yapacak JavaScript kodları şu şekilde:</p>

<pre class="lang:default decode:true">&lt;script type="text/javascript"&gt;
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
&lt;/script&gt;</pre>
<p style="text-align: justify;"><!--more-->Bunu ilgili yere eklemenin iki yolu var. Birincisi, "<em>Özellikleri Düzenle</em>" penceresi açıkken adres çubunun sonuna "<strong>&amp;ToolPaneView=2</strong>" ekleyip, sayfamıza bir "<em>İçerik Düzenleyicisi</em>" (<em>Content Editor</em>) web partı ekleyerek yukarıdaki kodu HTML içeriğine eklemek. İkinci yol için <em>SharePoint Designer</em> kullanarak sitemize bağlanmamız gerekiyor. Aşağıdaki resimde de gördüğünüz üzere sol tarafta bulunan "<em>List and Libraries</em>" bölümünden ilgili kütüphanemizi seçip, <strong>EditForm.aspx</strong> dosyamıza sağ tıklayıp bu dosyayı düzenlememiz gerekiyor. Aşağıdaki satırı bulup hemen altına yukarıdaki kodları ekleyip dosyamızı kaydedersek, açılan bu pencereyi savuşturmuş oluyoruz.</p>

<pre class="lang:default decode:true">&lt;asp:Content ContentPlaceHolderId="PlaceHolderMain" runat="server"&gt;</pre>
<img class="aligncenter size-full wp-image-375" src="http://www.hasangok.com.tr/wp-content/uploads/2013/10/sharepoint-designer.png" alt="sharepoint-designer" width="898" height="672" />
<p style="text-align: justify;">Ben bu yöntemi <em>SharePoint 2013</em> için kullandım ve başarılı oldum. Aynısı <em>SharePoint 2010</em> için de kullanılabilir. Yazının İngilizce versiyonuna <a title="Bypass Edit Properties Dialog After Uploading to a Document Library" href="http://www.hasangok.com.tr/383/bypass-edit-properties-dialog-after-uploading-to-a-document-library.html">buradan</a> ulaşabilirsiniz.</p>
