---
layout: post
title: SharePoint Listesi InfoPath Hatası
date: 2014-03-18 10:00
author: hasangok
comments: true
Tags: [InfoPath, Programlar, Sharepoint, SharePoint, sorun]
---
<p style="text-align: justify;"><img class="alignleft  wp-image-517" style="margin: 2px;" alt="infopath-logo" src="https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/12/infopath-logo.png" width="118" height="118" />Bu yazıyı okuyosanız <em>InfoPath</em> ile özelleştirdiğiniz bir <em>SharePoint</em> liste formunda şu hata ile karşılaşmışsınız demektir: <em>The data types of the following form fields do not match the SharePoint list</em>. Yeni oluşturduğunuz formları kaydedebiliyor olsanız da, bu hatayı muhtemelen daha önceden kaydettiklerinizi düzenlerken alıyorsunuz.</p>
<p style="text-align: justify;">Bu hatanın sebebi, birilerinin sizden habersiz listenizdeki bir kolonu silmesi / değiştirmesi ya da yeni bir kolon eklemiş olması olabilir. <em>InfoPath</em> ile formu tekrar özelleştirip, güncel halini yayınladığınız takdirde bu hatanın yok olması gerekiyor(<em>muş</em>). Ancak benim gibi siz de bunu zaten denemiş ve hatayı giderememiş olabilirsiniz. Bu durumda yapılacak tek iş Liste Ayarları (<em>List Settings</em>) &gt; Form Ayarları (<em>Form Settings</em>) yolunu izleyip <em>InfoPath</em> formunu tamamen silmeniz. Daha önceden düzenliyor olduğunuz formu bu işlemden sonra tekrar yayınlarsanız (<em>Publish</em>) hatanız ortadan kalkacaktır.</p>
<p style="text-align: justify;"><em>InfoPath</em> sevmeyenlere bir de iyi haber: sonu gelmiş, yakında işi bitecek. Bilgi sağlam kaynaktan :)</p>
<p style="text-align: justify;">Sevgiler...</p>
