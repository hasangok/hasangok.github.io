---
layout: post
title: SharePoint User Profile'daki Hatalı Profil Resmi URL'lerin Düzeltilmesi
date: 2013-10-28 15:48
author: hasangok
comments: true
Tags: [PowerShell, PowerShell, Profil Resmi, Sharepoint, SharePoint, User Profile]
---
<p style="text-align: justify;">Bu yazıma, yakın zamanda <em>Active Directory</em>'deki kullanıcı profil resimlerinin nasıl <em>SharePoint User Profile</em>'a çekilebileceğini açıklayan bir yazı da yazacağımı belirterek başlamak istiyorum. Ancak önce elimizdeki problemi çözelim ;)</p>
<p style="text-align: justify;">En son karşılaştığım ve çözmek zorunda olduğum sorun buydu: <em>Active Directory</em>'de tanımlı kullanıcı resimleri, <em>SharePoint User Profile</em>'a aktarılmıştı ancak tüm resim URL'leri hatalıydı. Bu yüzden <em>arama sonuçları</em> ve <em>My Site</em> gibi yerlerde kullanıcıların resimleri yerine çarpı işaretleri görüyorduk. <em>URL'deki problem ise site adresinden sonra tek bir '/' karakterinin eksik olmasıydı</em>.</p>
<p style="text-align: justify;">Profil resimlerinin URL'leri şu şekilde görünüyordu:</p>

<pre class="lang:default decode:true">http://sharepointURL/my/mysitesUser PhotosProfile Pictures/...</pre>
Oysa olması gereken URL şu şekildeydi:
<pre class="lang:default decode:true">http://sharepointURL/my/mysites/User PhotosProfile Pictures/...</pre>
Aşağıdaki <em>PowerShell</em> scriptini çalıştırarak, yukarıda ilk yazdığım formatta olan tüm URL'leri ikinci formata dönüştürmek mümkün oldu. Böylece sorunumuz da çözülmüş oldu.
<pre class="lang:default decode:true crayon-selected">Add-PSSnapin Microsoft.Sharepoint.Powershell 
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

$site.Dispose()</pre>
&nbsp;
