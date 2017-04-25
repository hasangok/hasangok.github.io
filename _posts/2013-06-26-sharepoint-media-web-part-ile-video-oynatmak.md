---
layout: post
title: SharePoint Media Web Part ile Video Oynatmak
date: 2013-06-26 16:46
author: hasangok
comments: true
Tags: [Javascript, Media Webpart, Sharepoint, SharePoint]
---
Son birkaç gündür Coca-Cola için bir video player web part’ı yazmaya çalışıyorum. Bunun için öncelikle "**flow player**" kullanmak istesem de, Internet Explorer’da çıkarttığı sorunlar yüzünden bundan vazgeçtim ve SharePoint içinde gelen "***Media Web Part***"ı kullanmaya karar verdim. Bu web part'ı sayfamıza dinamik olarak ekleyip istediğimiz video’yu oynatabiliyoruz. Bunun için öncelikle "***mediaplayer.js***" dosyasını sayfamıza eklememiz gerekiyor:

```html
<script type="text/javascript" src="/_layouts/mediaplayer.js"></script>
```
Daha sonra aşağıdaki kodları kullanarak media webpartımızı *videoDiv* adını vereceğimiz bir div içerisinde oluşturabiliyoruz.

```javascript
 $(document).ready(function () {
 var videoHolder = document.getElementById(‘videoDiv’);

mediaPlayer.createMediaPlayer(
 videoHolder, videoHolder.id, ’461px’, ’272px’,
 {
 displayMode: ‘Inline’,
 mediaTitle: ‘Başlık’,
 mediaSource: ‘Video URL’,
 previewImageSource: ”,
 autoPlay: false,
 loop: true,
 mediaFileExtensions: ‘wmv;wma;avi;mpg;mp3;’,
 silverlightMediaExtensions: ‘wmv;wma;mp3;’
 }
 );
 });
```
Not: ready() fonksiyonunu kullanmadığımız takdirde, sayfa yüklenmeden bu kodların çalışması ve istediğimiz div’in bulunamaması gibi bir sorun oluşabiliyor. Bu yüzden sayfa tamamen yüklenene kadar bu kodu bekletmek en doğrusu. .ready() fonksiyonu için Jquery, Jquery için aşağıdaki ifade gereklidir:

```html
<script type="text/javascript" src="./path/jquery.min.js"></script>
```
