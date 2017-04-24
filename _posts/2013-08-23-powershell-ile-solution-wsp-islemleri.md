---
layout: post
title: PowerShell ile Solution (wsp) İşlemleri
date: 2013-08-23 14:35
author: hasangok
comments: true
Tags: [PowerShell, Sharepoint, SharePoint, wsp]
---
<em>SharePoint</em> projelerimizi <strong>Publish</strong> edip <em>wsp paketi</em>mizi aldıktan sonra, <em>PoweShell</em> kullanarak bu paketi <em>yüklemek</em>, <em>deploy etmek</em>, <em>güncellemek</em>, <em>retract etmek</em> ve <em>silmek</em> için aşağıdaki komutları kullanıyoruz.

<strong>Ekleme:</strong>
<pre class="brush: sql;">Add-SPSolution "C:\Solutions\SharePointSolution.wsp"</pre>
<strong>Yükleme:</strong>
<pre class="brush: sql;">Install-SPSolution –Identity SharePointSolution.wsp –WebApplication http://url –GACDeployment</pre>
Eğer <em>sandboxed</em> bir solution yükleyeceksek aşağıdaki komutu kullanıyoruz:
<pre class="brush: sql;">Install-SPUserSolution –Identity SharePointSolution.wsp –WebApplication http://url –GACDeployment</pre>
<strong>Güncelleme:</strong>
<pre class="brush: sql;">Update-SPSolution –Identity SharePointSolution.wsp –LiteralPath "C:\Solutions\SharePointSolution.wsp" –GacDeployment</pre>
<strong>Kaldırma:</strong>
<pre class="brush: sql;">Uninstall-SPSolution –Identity SharePointSolution.wsp –WebApplication http://url</pre>
<strong>Silme:</strong>
<pre class="brush: sql;">Remove-SPSolution–Identity SharePointSolution.wsp</pre>
