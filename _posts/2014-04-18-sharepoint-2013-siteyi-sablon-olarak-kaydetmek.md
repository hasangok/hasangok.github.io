---
layout: post
title: SharePoint 2013 - Siteyi Şablon Olarak Kaydetmek
date: 2014-04-18 12:06
author: hasangok
comments: true
Tags: [Save Site As Template, SharePoint, Sharepoint 2013, SharePoint Designer]
---
<p style="text-align: justify;"><em>SharePoint 2013</em> sitenizi şablon olarak kaydetmek için <em>Site Eylemleri</em> (<em>Site Actions</em>) altındaki <strong><em>Siteyi şablon olarak kaydet</em></strong> (<em>Save Site As Template</em>) linkini kullanabiliyoruz. Ancak bu link aktif değilse ve görünmüyorsa ne yapacağız?</p>
<p style="text-align: justify;"><!--more--></p>
<p style="text-align: justify;"><em>SharePoint Designer</em>'ı açıp sitemize bağlandıktan sonra ribbonda bulunan <em><strong>Site Options</strong></em> butonuna tıklıyor ve değeri "<em>false</em>" olan <em><strong>SaveSiteAsTemplateEnabled</strong></em> parametresini "<em>true</em>" olarak değiştiriyoruz.</p>
<p style="text-align: justify;"><img class="aligncenter size-full wp-image-684" src="http://www.hasangok.com.tr/wp-content/uploads/2014/04/save-site-as-template.png" alt="save-site-as-template" width="413" height="354" /></p>
<p style="text-align: justify;">Bu değişiklikten sonra ilgili linki görebiliyor olmamız lazım. Eğer göremiyorsak sayfaya direk <em>http://siteadresi/_layouts/15/savetmpl.aspx</em> adresinden ulaşabilir ve sitemizin şablonunu alabiliriz. Aynı sorunla karşılaşmamız durumunda tabi ki <em>SharePoint 2010</em> için de aynı adımları takip edebiliriz.</p>
<p style="text-align: justify;">Kolay gelsin.</p>
