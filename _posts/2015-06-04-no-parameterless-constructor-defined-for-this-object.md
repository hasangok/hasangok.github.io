---
layout: post
title: No parameterless constructor defined for this object
date: 2015-06-04 14:02
author: hasangok
comments: true
Tags: [Genel, Page Layout, Publishing Page]
---
Kod tarafında bir page layout'tan türeyen publishing page oluştururken başlıktaki hatayı alabiliyoruz. Sebeplerinden bazıları şunlar olabilir:
<ol>
	<li>Page Layout içerisindeki <strong>&lt;asp:content&gt;</strong> atiketlerinin <strong>&lt;asp:Content&gt;</strong> olması gerekiyor. Content'in büyük harfle başlaması şart.</li>
	<li>Page Layout'u bir feature ile deploy ettiysek <strong>&lt;AllUsersWebPart&gt;&lt;/AllUsersWebPart&gt;</strong> içerisinin boş kalmış olması.</li>
	<li><strong>&lt;AllUsersWebPart&gt;&lt;/AllUsersWebPart&gt;</strong> içerisinde deploy edilen Web Part custom geliştirilmiş ise, beklediği parametrelerin eksik bırakılmış olması.</li>
</ol>
