---
layout: post
title: List Form WebPart Yerine Data Form WebPart Eklemek ve Buton Düzenlemesi
date: 2013-11-15 09:23
author: hasangok
comments: true
Tags: [Data Form Web Part, GenFireServerEvent, JavaScript, Sharepoint, SharePoint, SharePoint-GoBackButton, XSL]
---
<p style="text-align: justify;"><strong>SharePoint 2010</strong> kullananların en çok gördüğü pencerelerden biridir sanırım aşağıdaki pencere (en azından benim için öyle). Evet, doğru tahmin ettiniz. Bu pencereyle alakalı bir sorun yaşayıp yeni bir şey öğrendiğim için, bunu sizlerle de paylaşıyorum ;)</p>
<img class="aligncenter size-full wp-image-459" alt="sharepoint-2010-add-new-item" src="http://www.hasangok.com.tr/wp-content/uploads/2013/11/sharepoint-2010-add-new-item.png" width="623" height="307" />
<p style="text-align: justify;">Varsayalım ki listemize yeni bir kayıt giriyoruz, ekranımızda yukarıda gördüğünüz pencere varken tarayıcımızın adres çubuğunda şu URL görünüyor:</p>

<pre class="lang:default decode:true">http://sharepointURL/Lists/Test/NewForm.aspx?Source=/Pages/Kaydedildi.aspx</pre>
<p style="text-align: justify;">Biliyoruz ki kaydımızı girmek için <em>Kaydet</em> (<strong>Save</strong>) butonuna bassak da, vazgeçip <em>İptal</em> (<strong>Cancel</strong>) butonuna bassak da, URL'de <strong>Source</strong> parametresiyle belirtilen "<em>/Pages/Kaydedildi.aspx</em>" sayfasına yönlendirileceğiz. Peki, <em>Kaydet</em> butonuna basınca bu sayfaya gidip <em>İptal</em> butonuna basınca başka bir sayfaya gitmek istiyorsak ne yapacağız? Bu soruya verdiğim ilk cevap bir <em>JavaScript</em> kodu yazıp <em>İptal</em> butonuna tıklandığında istediğimiz sayfaya yönlendirmek şeklinde oldu. Hatta şu şekilde hemen bu isteği gerçekleştirebildim:</p>
<p style="text-align: justify;"><!--more--></p>

<pre class="lang:default decode:true">$(document).ready(function() {
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
});</pre>
<p style="text-align: justify;">Bu tabi ki bir çözümdü. Ancak <em>JavaScript</em> kodlarının client bazında farklı davranabiliyor olması yüzünden, liste üzerindeki ekleme, düzenleme vb. işlemlerde <em>JavaScript</em> ile değil, <em>XSL</em> ile değişiklikler yapmanın doğru ve uygun bir yöntem olduğunu öğrendim. Hal böyle olunca yapılması gereken, listemizin <strong>NewForm.aspx</strong> dosyasında düzenleme yapmak oldu. Bunun için aşağıdaki adımları takip edebilirsiniz:</p>

<ol>
	<li style="text-align: justify;"><em>SharePoint Designer 2010</em> ile sitemize bağlanıp ilgili listeyi bulduktan sonra, <em>NewForm.aspx</em> dosyasına sağ tıklayıp "<strong>Edit File in Advanced Mode</strong>" seçeneğine tıklıyoruz.
<img class="aligncenter size-full wp-image-465" alt="newform.aspx" src="http://www.hasangok.com.tr/wp-content/uploads/2013/11/newform.aspx_.png" width="656" height="156" /></li>
	<li style="text-align: justify;">Tasarım (Design) moduna geçip List Form Web Part'ın önizlemesine tıklayarak tekrar kodlara döndüğümüzde seçili olan kod bloğunu siliyoruz.
<img class="aligncenter size-full wp-image-460" alt="sharepoint-designer-listformwebpart" src="http://www.hasangok.com.tr/wp-content/uploads/2013/11/sharepoint-designer-listformwebpart.png" width="675" height="425" /></li>
	<li style="text-align: justify;">Sildiğimiz yerde kalmak şartıyla (aynı zone içerisinde) <em>Ribbon</em>'daki <strong>Insert</strong> menüsünden <strong>New Item Form</strong> butonuna tıklayıp <strong>Custom List Form</strong> seçeneğine tıklıyoruz.
<img class="aligncenter size-full wp-image-461" alt="sharepoint-designer-custom-list-form" src="http://www.hasangok.com.tr/wp-content/uploads/2013/11/sharepoint-designer-custom-list-form.png" width="713" height="445" /></li>
	<li style="text-align: justify;">Gelen pencerede ilgili listemizi ve <em>New Item Form</em>'u seçerek <strong>OK</strong> diyoruz.</li>
</ol>
<p style="text-align: justify;">Bu aşamada <em>List Form Web Part</em>'ı sayfamızdan silip yerine <em>Data Form Web Part</em> eklemiş oluyoruz. Artık butonlarla uğraşabiliriz.</p>
<img class="aligncenter size-full wp-image-462" alt="sharepoint-designer-data-form-web-part" src="http://www.hasangok.com.tr/wp-content/uploads/2013/11/sharepoint-designer-data-form-web-part.png" width="702" height="462" />
<p style="text-align: justify;">Tasarım moduna geçip yeni eklenen web partı incelersek, <em>List Form Web Part</em>'ın aksine sayfa içerisindeki elemanlara ulaşıp bunları düzenleyebildiğimizi göreceğiz. Konumuz olan <em>İptal</em> (<strong>Cancel</strong>) butonlarına geri dönelim. Kodumuzda aşağıdaki iki satırı bulalım:</p>

<pre class="lang:default decode:true">&lt;SharePoint:GoBackButton runat="server" ControlMode="New" id="gobackbutton1"/&gt;
&lt;SharePoint:GoBackButton runat="server" ControlMode="New" id="gobackbutton2"/&gt;</pre>
<p style="text-align: justify;">Bu iki satırı aşağıdaki kod ile değiştirelim:</p>

<pre class="lang:default decode:true">&lt;input type="button" class="ms-ButtonHeightWidth" value="İptal" name="btnCancel" onclick="javascript: {ddwrt:GenFireServerEvent('__redirect={/Pages/IptalEdildi.aspx}')}" /&gt;</pre>
<p style="text-align: justify;">Bu değişikliği yaptıktan sonra dosyamızı kaydedersek göreceğiz ki <em>Kaydet</em> (<strong>Save</strong>) butonu bizi URL'deki <em>Source</em> ile belirtilen "<em>/Pages/Kaydedildi.aspx</em>" adresine yönlendirirken, <em>İptal</em> (<strong>Cancel</strong>) butonu <strong>GenFireServerEvent</strong> içerisinde belirttiğimiz "<em>/Pages/IptalEdildi.aspx</em>" sayfasına yönlendirecek.</p>
