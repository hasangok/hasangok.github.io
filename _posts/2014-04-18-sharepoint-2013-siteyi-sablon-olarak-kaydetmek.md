---
layout: post
title: SharePoint 2013 - Siteyi Şablon Olarak Kaydetmek
date: 2014-04-18 12:06
author: hasangok
comments: true
Tags: [Save Site As Template, SharePoint, Sharepoint 2013, SharePoint Designer]
---
*SharePoint 2013* sitenizi şablon olarak kaydetmek için *Site Eylemleri* (*Site Actions*) altındaki ***Siteyi şablon olarak kaydet*** (*Save Site As Template*) linkini kullanabiliyoruz. Ancak bu link aktif değilse ve görünmüyorsa ne yapacağız?

*SharePoint Designer*'ı açıp sitemize bağlandıktan sonra ribbonda bulunan ***Site Options*** butonuna tıklıyor ve değeri "*false*" olan ***SaveSiteAsTemplateEnabled*** parametresini "*true*" olarak değiştiriyoruz.

![save-site-as-template](https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2014/04/save-site-as-template.png "save-site-as-template")

Bu değişiklikten sonra ilgili linki görebiliyor olmamız lazım. Eğer göremiyorsak sayfaya direk *http://siteadresi/_layouts/15/savetmpl.aspx* adresinden ulaşabilir ve sitemizin şablonunu alabiliriz. Aynı sorunla karşılaşmamız durumunda tabi ki *SharePoint 2010* için de aynı adımları takip edebiliriz.
Kolay gelsin.