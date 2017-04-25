---
layout: post
title: JavaScript Client Object Model ile Liste İşlemleri
date: 2014-01-13 16:00
author: hasangok
comments: true
Tags: [Client Object Model, JavaScript, Liste İşlemleri, Sharepoint, SharePoint]
---
<p style="text-align: justify;"><img class="alignleft  wp-image-342" alt="SharePoint2010" src="https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/09/SharePoint2010.jpg" width="122" height="95" />Bu konuyla alakalı detaylıca bir yazı hazırlama düşüncesi çok uzun zamandır aklımda ancak bir türlü gereken vakti ayıramıyorum. O yüzden detayları bir kenara bırakıp, işe girdim gireli belki de en çok kullandığım bu <em>JavaScript</em> liste işlemlerini sizlerle de paylaşmak istedim. Avantaj ve dezavantajlarından <a title="Client Object Model – Avantaj ve Dezavantajlar" href="http://www.hasangok.com.tr/272/client-object-model-avantaj-ve-dezavantajlar.html">burada</a> bahsettiğim konunun kod kısmını aşağıdan görebilir ve kullanabilirsiniz.</p>
<p style="text-align: justify;"><!--more--></p>
<p style="text-align: justify;"><strong>Listeye Öge Ekleme:</strong></p>

<pre class="lang:default decode:true">var myContext = new SP.ClientContext.get_current();
var myWeb = myContext.get_web();
var myList = myWeb.get_lists().getByTitle('ListeAdı');
var myListItemCreationInfo = new SP.ListItemCreationInformation();
var newItem = myList.addItem(myListItemCreationInfo);
newItem.set_item('Title', titleText);
newItem.update();

myContext.executeQueryAsync(Function.createDelegate(this, AddNewItemSuccess),
      Function.createDelegate(this, AddNewItemFail));

function AddNewItemFail(sender, args) {
   alert('Yeni öge eklenemedi: ' + args.get_message());
}
function AddNewItemSuccess(sender, args) {
   alert('Yeni öge başarıyla eklendi.');
}</pre>
<p style="text-align: justify;"><strong>Liste Ögelerine Ulaşma:</strong></p>

<pre class="lang:default decode:true">ExecuteOrDelayUntilScriptLoaded(function () {
   var context = new SP.ClientContext.get_current();
   var web = context.get_web();
   var list = web.get_lists().getByTitle('ListeAdı');

   var query = SP.CamlQuery.createAllItemsQuery();
   allItems = list.getItems(query);
   context.load(allItems);

   context.executeQueryAsync(Function.createDelegate(this, GetItemsSuccess),
      Function.createDelegate(this, GetItems.Failed));
}, 'sp.js');

function GetItemsSuccess() {
   var ListEnumerator = this.allItems.getEnumerator();
   while (ListEnumerator.moveNext()) {
      var currentItem = ListEnumerator.get_current();
      alert(currentItem.get_item('Title'));    
   }
}

function GetItemsFailed(sender, args) {
   alert("Ögelere ulaşılamadı: " + args.get_message());
}</pre>
<p style="text-align: justify;"><strong>Liste Ögesini Güncelleme:</strong></p>

<pre class="lang:default decode:true">var myContext = new SP.ClientContext.get_current();
var myWeb = myContext.get_web();
var myList = myWeb.get_lists().getByTitle('ListeAdı');
var myListItem = myList.getItemById(2014);
myListItem.set_item('Title', 'Hasan');
myListItem.update();

myContext.executeQueryAsync(Function.createDelegate(this, UpdateItemSuccess),
      Function.createDelegate(this, UpdateItemFail));

function UpdateItemFail(sender, args) {
   alert('Öge güncellenemedi: ' + args.get_message());
}
function UpdateItemSuccess(sender, args) {
   alert('Öge başarıyla güncellendi.');
}</pre>
<p style="text-align: justify;"><strong>Listeden Öge Silme:</strong></p>

<pre class="lang:default decode:true ">var myContext = new SP.ClientContext.get_current();
var myWeb = myContext.get_web();
var myList = myWeb.get_lists().getByTitle('ListeAdı');
var myListItem = myList.getItemById(2014);
myListItem.deleteObject();

myContext.executeQueryAsync(Function.createDelegate(this, DeleteItemSuccess),
      Function.createDelegate(this, DeleteItemFail));

function DeleteItemFail(sender, args) {
   alert('Öge silinemedi: ' + args.get_message());
}
function DeleteItemSuccess(sender, args) {
   alert('Öge başarıyla silindi.');
}</pre>
<p style="text-align: justify;">Vakit ayırabilirsem bir sonraki yazı, bir <em>jQuery</em> eklentisi olan <em>SPServices</em> ile ilgili olacak, bunun haberini de -kendimi yazmaya motive edebilmek adına- vermiş olayım.</p>
<p style="text-align: justify;">Hepinize iyi çalışmalar...</p>
