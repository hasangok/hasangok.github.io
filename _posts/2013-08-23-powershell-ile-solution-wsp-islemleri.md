---
layout: post
title: PowerShell ile Solution (wsp) İşlemleri
date: 2013-08-23 14:35
author: hasangok
comments: true
Tags: [PowerShell, Sharepoint, SharePoint, wsp]
---
*SharePoint* projelerimizi **Publish** edip *wsp paketi*mizi aldıktan sonra, *PoweShell* kullanarak bu paketi *yüklemek*, *deploy etmek*, *güncellemek*, *retract etmek* ve *silmek* için aşağıdaki komutları kullanıyoruz.

**Ekleme:**
```powershell
Add-SPSolution "C:\Solutions\SharePointSolution.wsp"
```
**Yükleme:**
```powershell
Install-SPSolution –Identity SharePointSolution.wsp –WebApplication http://url –GACDeployment
```
Eğer *sandboxed* bir solution yükleyeceksek aşağıdaki komutu kullanıyoruz:
```powershell
Install-SPUserSolution –Identity SharePointSolution.wsp –WebApplication http://url –GACDeployment
```
**Güncelleme:**
```powershell
Update-SPSolution –Identity SharePointSolution.wsp –LiteralPath "C:\Solutions\SharePointSolution.wsp" –GacDeployment
```
**Kaldırma:**
```powershell
Uninstall-SPSolution –Identity SharePointSolution.wsp –WebApplication http://url
```
**Silme:**
```powershell
Remove-SPSolution–Identity SharePointSolution.wsp
```