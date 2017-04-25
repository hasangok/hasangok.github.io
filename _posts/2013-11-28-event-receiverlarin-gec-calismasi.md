---
layout: post
title: Event Receiver'ların Geç Çalışması
date: 2013-11-28 15:15
author: hasangok
comments: true
Tags: [Event Receiver, Sharepoint, SharePoint]
---
![SharePoint-2010-Logo](https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/12/SharePoint-2010-Logo.png)
Birkaç gündür büyük sıkıntıya sebep oldu bu durum. Bir *Event Receiver* ile *ItemAdded* ve *ItemUpdated* olaylarında, belirlenmiş bir alanı bildiğimiz bir değer ile güncellemeye çalışıyorum. Tabi ki güncelleyebiliyorum ancak *Event Receiver*'ımız bunu biraz geç yaptığından ilgili alanın dolduğunu görmek için sayfayı yenilemem gerekiyor, ki bu hiç istemediğimiz bir durum. İstenmeyen bu durumdan kurtulmak aslında çok basit(*miş*). Varsayılan olarak asenkron (*asynchronous*) çalışan bu receiverlara, senkron (*synchronous*) çalışması için aşağıdaki gibi bir tanımlama yapmamız yeterli oluyor:

```xml
<?xml version="1.0" encoding="utf-8"?>
<Elements xmlns="http://schemas.microsoft.com/sharepoint/">
  <Receivers ListTemplateId="104">
    <Receiver>
      <Name>SetPeopleERItemUpdated</Name>
      <Type>ItemUpdated</Type>
      <Assembly>$SharePoint.Project.AssemblyFullName$</Assembly>
      <Class>EventRecivers.SetPeopleER.SetPeopleER</Class>
      <SequenceNumber>1000</SequenceNumber>
      <Synchronization>Synchronous</Synchronization>
    </Receiver>
    <Receiver>
      <Name>SetPeopleERItemAdded</Name>
      <Type>ItemAdded</Type>
      <Assembly>$SharePoint.Project.AssemblyFullName$</Assembly>
      <Class>EventRecivers.SetPeopleER.SetPeopleER</Class>
      <SequenceNumber>1000</SequenceNumber>
      <Synchronization>Synchronous</Synchronization>
    </Receiver>
  </Receivers>
</Elements>
```
Artık liste veya kütüphanenize bir öge eklediğinizde ya da güncellediğinizde, ilgili alan da Event Receiver'ımız tarafından derhal güncellenmiş olacak. Detaylar için [buraya(http://msdn.microsoft.com/en-US/library/gg981880.aspx) bakabilirsiniz.
Kolay gelsin.
