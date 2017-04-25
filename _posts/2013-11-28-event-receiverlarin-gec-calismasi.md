---
layout: post
title: Event Receiver'ların Geç Çalışması
date: 2013-11-28 15:15
author: hasangok
comments: true
Tags: [Event Receiver, Sharepoint, SharePoint]
---
<p style="text-align: justify;"><img class="alignleft  wp-image-493" style="margin: 0px 2px; border: 0px;" alt="SharePoint-2010-Logo" src="https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/12/SharePoint-2010-Logo-150x150.png" width="105" height="105" />Birkaç gündür büyük sıkıntıya sebep oldu bu durum. Bir <em>Event Receiver</em> ile <em>ItemAdded</em> ve <em>ItemUpdated</em> olaylarında, belirlenmiş bir alanı bildiğimiz bir değer ile güncellemeye çalışıyorum. Tabi ki güncelleyebiliyorum ancak <em>Event Receiver</em>'ımız bunu biraz geç yaptığından ilgili alanın dolduğunu görmek için sayfayı yenilemem gerekiyor, ki bu hiç istemediğimiz bir durum. İstenmeyen bu durumdan kurtulmak aslında çok basit(<em>miş</em>). Varsayılan olarak asenkron (<em>asynchronous</em>) çalışan bu receiverlara, senkron (<em>synchronous</em>) çalışması için aşağıdaki gibi bir tanımlama yapmamız yeterli oluyor:</p>
<p style="text-align: justify;"><!--more--></p>

<pre class="lang:default decode:true">&lt;?xml version="1.0" encoding="utf-8"?&gt;
&lt;Elements xmlns="http://schemas.microsoft.com/sharepoint/"&gt;
  &lt;Receivers ListTemplateId="104"&gt;
    &lt;Receiver&gt;
      &lt;Name&gt;SetPeopleERItemUpdated&lt;/Name&gt;
      &lt;Type&gt;ItemUpdated&lt;/Type&gt;
      &lt;Assembly&gt;$SharePoint.Project.AssemblyFullName$&lt;/Assembly&gt;
      &lt;Class&gt;EventRecivers.SetPeopleER.SetPeopleER&lt;/Class&gt;
      &lt;SequenceNumber&gt;1000&lt;/SequenceNumber&gt;
      &lt;Synchronization&gt;Synchronous&lt;/Synchronization&gt;
    &lt;/Receiver&gt;
    &lt;Receiver&gt;
      &lt;Name&gt;SetPeopleERItemAdded&lt;/Name&gt;
      &lt;Type&gt;ItemAdded&lt;/Type&gt;
      &lt;Assembly&gt;$SharePoint.Project.AssemblyFullName$&lt;/Assembly&gt;
      &lt;Class&gt;EventRecivers.SetPeopleER.SetPeopleER&lt;/Class&gt;
      &lt;SequenceNumber&gt;1000&lt;/SequenceNumber&gt;
      &lt;Synchronization&gt;Synchronous&lt;/Synchronization&gt;
    &lt;/Receiver&gt;
  &lt;/Receivers&gt;
&lt;/Elements&gt;</pre>
<p style="text-align: justify;">Artık liste veya kütüphanenize bir öge eklediğinizde ya da güncellediğinizde, ilgili alan da Event Receiver'ımız tarafından derhal güncellenmiş olacak. Detaylar için <a href="http://msdn.microsoft.com/en-US/library/gg981880.aspx" target="_blank">buraya</a> bakabilirsiniz.
Kolay gelsin.</p>
