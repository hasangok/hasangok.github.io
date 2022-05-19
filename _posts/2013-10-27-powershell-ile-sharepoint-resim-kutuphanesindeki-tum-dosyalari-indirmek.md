---
title: PowerShell ile SharePoint Resim Kütüphanesindeki Dosyaları İndirmek
date: 2013-10-27 14:34
---

Birkaç *PowerShell* scripti ile ilgilenmek zorunda kaldıktan sonra, böyle bir şey de vardı diyen arkadaşım Selçuk Demir aracılığıyla paylaşıyorum efendim 🙂 *SharePoint 2010* ve *SharePoint 2013* resim kütüphanelerinde deneyip başarılı çalıştığını gördüğümüz bu scriptin ilgili değişkenlerini düzenleyip, kütüphanenizde bulunan tüm resimleri belirlediğiniz bir klasöre indirebiliyorsunuz.

<!--more-->
```powershell
Remove-PSSnapin Microsoft.SharePoint.PowerShell -erroraction SilentlyContinue
Add-PSSnapin Microsoft.SharePoint.PowerShell -erroraction SilentlyContinue

$destination = "C:\MyLibrary"
$webUrl = "http://sharepointURL"
$listUrl = "http://sharepointURL/PictureLibrary"

$web = Get-SPWeb -Identity $webUrl
$list = $web.GetList($listUrl)

function DownLoadImages($folderUrl)
{
    $folder = $web.GetFolder($folderUrl)
    foreach ($file in $folder.Files)
    {
        $destinationfolder = $destination + "/" + $folder.Url
        if (!(Test-Path -path $destinationfolder))
        {
            $dest = New-Item $destinationfolder -type directory
        }
        $binary = $file.OpenBinary()
        $stream = New-Object System.IO.FileStream($destinationfolder + "/" + $file.Name), Create
        $writer = New-Object System.IO.BinaryWriter($stream)
        $writer.write($binary)
        $writer.Close()
    }
}

try
{ 
    DownLoadImages($list.RootFolder.Url)
    foreach ($folder in $list.Folders)
    {
        DownLoadImages($folder.Url)
    }
}
catch
{
    write-host $_.exception 
}
finally
{
    if($web -ne $null)
    {
        $web.Dispose()
    }
}
```