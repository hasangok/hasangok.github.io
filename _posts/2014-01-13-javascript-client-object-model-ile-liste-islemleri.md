---
layout: post
title: JavaScript Client Object Model ile Liste İşlemleri
date: 2014-01-13 16:00
author: hasangok
comments: true
Tags: [Client Object Model, JavaScript, Liste İşlemleri, Sharepoint, SharePoint]
---
![SharePoint2010](https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/09/SharePoint2010.jpg)
Bu konuyla alakalı detaylıca bir yazı hazırlama düşüncesi çok uzun zamandır aklımda ancak bir türlü gereken vakti ayıramıyorum. O yüzden detayları bir kenara bırakıp, işe girdim gireli belki de en çok kullandığım bu *JavaScript* liste işlemlerini sizlerle de paylaşmak istedim. Avantaj ve dezavantajlarından [burada](http://www.hasangok.com.tr/272/client-object-model-avantaj-ve-dezavantajlar.html) bahsettiğim konunun kod kısmını aşağıdan görebilir ve kullanabilirsiniz.

**Listeye Öge Ekleme:**
```javascript
var myContext = new SP.ClientContext.get_current();
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
}
```
**Liste Ögelerine Ulaşma:**

```javascript
ExecuteOrDelayUntilScriptLoaded(function () {
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
}
```
**Liste Ögesini Güncelleme:**

```javascript
var myContext = new SP.ClientContext.get_current();
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
}
```
**Listeden Öge Silme:**

```javascript
var myContext = new SP.ClientContext.get_current();
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
}
```
Vakit ayırabilirsem bir sonraki yazı, bir *jQuery* eklentisi olan *SPServices* ile ilgili olacak, bunun haberini de -kendimi yazmaya motive edebilmek adına- vermiş olayım.
Hepinize iyi çalışmalar...
