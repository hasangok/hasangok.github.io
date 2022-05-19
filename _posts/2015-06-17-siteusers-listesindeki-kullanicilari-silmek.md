---
title: SiteUsers Listesindeki Kullanıcıları Silmek
date: 2015-06-17 12:03
---

SharePoint Content DB'yi taşıyarak yeni bir ortama geçtiğimizde **SiteUsers** listesindeki kullanıcılar da olduğu gibi gelmiş oluyor. İstenmeyen bu durumu ortadan kaldırmak için kullanıcı adlarındaki bir metni filtre olarak kullanıp bunları silebiliriz. Son çalışmamızda ihtiyacımız, geliştirdiğimiz custom membership provider üzerinden gelen kullanıcıların silinmesiydi. Bunun için aşağıdaki PowerShell scriptini çalıştırdık.

<!--more-->
```powershell
$siteUrl = "http://sharepoint"
$filter = "membershipprovider"
 
$site = new-object Microsoft.SharePoint.SPSite($siteUrl)
$web = $site.OpenWeb()
 
$usersToDelete = @()
foreach ($user in $web.SiteUsers)
{
    if ($user.LoginName.ToLower().Contains( $filter ))
    {
        $usersToDelete += $user.LoginName
    }
}

foreach ($user in $usersToDelete)
{
    "Removing user : " + $user
    $web.SiteUsers.Remove($user);
}
 
$web.Update();
```

İyi çalışmalar...
