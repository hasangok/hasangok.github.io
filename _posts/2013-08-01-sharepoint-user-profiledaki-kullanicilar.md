---
title: Sharepoint User Profile'daki Kullanıcılar
date: 2013-08-01 12:02
---

Dört aydır Sharepoint geliştirme ile uğraşmaktayım. Sharepoint'in bir çok kavramı üzerinde en azından kulak aşinalığı oluşturmuş durumdayım. Ancak hiçbir fikrim olmayan bir konu vardı ki o da User Profile'dı. Küçük bir örnek ile Sharepoint'teki tüm kullanıcıların bilgilerine ulaştım, ihtiyacı olanlarla da paylaşmak istedim.

<!--more-->
Öncelikle Visual Studio'da bir Sharepoint projesi açıp, projemize Visual Web Part ekliyoruz. ASCX dosyamıza bir label ekleyip, Page_Load fonksiyonunu aşağıdaki gibi düzenliyoruz:

```csharp
protected void Page_Load(object sender, EventArgs e)
{
    SPServiceContext context = SPServiceContext.GetContext(SPContext.Current.Site);
    UserProfileManager profileManager = new UserProfileManager(context);
    lblUsers.Text = "<table border='1'><tr><th>UserGuid</th><th>AccountName</th><th>UserName</th></tr>";
    foreach (Microsoft.Office.Server.UserProfiles.UserProfile item in profileManager)
    {
    lblUsers.Text += "<tr><td>" + (item[PropertyConstants.AccountName] != null ? item[PropertyConstants.UserGuid].Value : "") +
    "</td><td>" + (item[PropertyConstants.UserGuid] != null ? item[PropertyConstants.AccountName].Value : "") +
    "</td><td>" + (item[PropertyConstants.UserName] != null ? item[PropertyConstants.UserName].Value : "") + "</td></tr>";
    }
    lblUsers.Text += "</table>";
}
```

Bu web part'ı herhangi bir sayfaya eklediğimizde tüm kullanıcılarımızı ve bilgilerini görebiliyoruz.

![sharepoint-users](/uploads/2013/08/sharepoint-users.png)
