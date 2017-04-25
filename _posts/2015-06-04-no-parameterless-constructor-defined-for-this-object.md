---
layout: post
title: No parameterless constructor defined for this object
date: 2015-06-04 14:02
author: hasangok
comments: true
Tags: [Genel, Page Layout, Publishing Page]
---
Kod tarafında bir page layout'tan türeyen publishing page oluştururken başlıktaki hatayı alabiliyoruz. Sebeplerinden bazıları şunlar olabilir:

1. Page Layout içerisindeki **&lt;asp:content&gt;** atiketlerinin **&lt;asp:Content&gt;** olması gerekiyor. Content'in büyük harfle başlaması şart.
2. Page Layout'u bir feature ile deploy ettiysek **&lt;AllUsersWebPart&gt;&lt;/AllUsersWebPart&gt;** içerisinin boş kalmış olması.
3. **&lt;AllUsersWebPart&gt;&lt;/AllUsersWebPart&gt;** içerisinde deploy edilen Web Part custom geliştirilmiş ise, beklediği parametrelerin eksik bırakılmış olması.

