---
title: SharePoint User Profile'daki Hatalı Profil Resmi URL'lerin Düzeltilmesi
date: 2013-10-28 15:48
---

Bu yazıma, yakın zamanda *Active Directory*'deki kullanıcı profil resimlerinin nasıl *SharePoint User Profile*'a çekilebileceğini açıklayan bir yazı da yazacağımı belirterek başlamak istiyorum. Ancak önce elimizdeki problemi çözelim 😉

<!--more-->
En son karşılaştığım ve çözmek zorunda olduğum sorun buydu: *Active Directory*'de tanımlı kullanıcı resimleri, *SharePoint User Profile*'a aktarılmıştı ancak tüm resim URL'leri hatalıydı. Bu yüzden *arama sonuçları* ve *My Site* gibi yerlerde kullanıcıların resimleri yerine çarpı işaretleri görüyorduk. *URL'deki problem ise site adresinden sonra tek bir '/' karakterinin eksik olmasıydı*.
Profil resimlerinin URL'leri şu şekilde görünüyordu:

```
http://sharepointURL/my/mysitesUser PhotosProfile Pictures/...
```
Oysa olması gereken URL şu şekildeydi:
```
http://sharepointURL/my/mysites/User PhotosProfile Pictures/...
```
Aşağıdaki *PowerShell* scriptini çalıştırarak, yukarıda ilk yazdığım formatta olan tüm URL'leri ikinci formata dönüştürmek mümkün oldu. Böylece sorunumuz da çözülmüş oldu.
```powershell
Add-PSSnapin Microsoft.Sharepoint.Powershell 
$SiteCollectionUrl = "http://sharepointURL/"
$hataliURL = "http://sharepointURL/my/mysitesUser" 
$dogruURL = "http://sharepointURL/my/mysites/User" 
$site = Get-SPSite $SiteCollectionUrl
$context = Get-SPServiceContext($site) 
$profileManager = new-object Microsoft.Office.Server.UserProfiles.UserProfileManager($context) 
Write-Host "profileManager.Count: " $profileManager.Count -ForegroundColor Yellow;

$profiles = $profileManager.GetEnumerator()
foreach ($userProfile in $profiles)
{
   if($userProfile["PictureUrl"].Value -ne $null)
   {
      Write-Host "AccountName: " $userProfile["AccountName"].Value ", PictureUrl: " $userProfile["PictureUrl"].Value -ForegroundColor Yellow;

      $eskiURL = $userProfile["PictureUrl"].Value
      if($eskiURL -match $hataliURL)
      {
         $userProfile["PictureUrl"].Value = $eskiURL.Replace($hataliURL, $dogruURL)
         $userProfile.Commit()
         Write-Host "new PictureUrl: " $userProfile["PictureUrl"].Value -ForegroundColor Yellow;
      }
   }
}

$site.Dispose()
```
