---
layout: post
title: SharePoint 2016 SPUpgradeException - One or more types failed to load.
date: 2017-05-04 11:45
author: hasangok
comments: true
Tags: [SharePoint, SharePoint 2016]
---
Yeni kurduğumuz bir SharePoint 2016 Farm'ında ilk kez Configuration Wizard çalıştırdığımda yukarıdaki hata ile karşılaşıyordum. Configuration Wizard çalışırken ULS loglarını izlediğimde aşağıdaki satırları gördüm:

```
ERROR Failed to call GetTypes() 00000000-0000-0000-0000-000000000000	 
ERROR Exception: Could not load file or assembly 'Microsoft.Data.Edm, Version=5.6.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35' or one of its dependencies. The system cannot find the file specified. 00000000-0000-0000-0000-000000000000	 
ERROR Failed to call GetTypes() 00000000-0000-0000-0000-000000000000	 
ERROR Exception: Could not load file or assembly 'Microsoft.Data.OData, Version=5.6.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35' or one of its dependencies. The system cannot find the file specified. 00000000-0000-0000-0000-000000000000	 
ERROR Failed to call GetTypes() 00000000-0000-0000-0000-000000000000	 
ERROR Exception: Could not load file or assembly 'Microsoft.Data.OData, Version=5.6.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35' or one of its dependencies. The system cannot find the file specified. 00000000-0000-0000-0000-000000000000	 
ERROR Failed to call GetTypes() 00000000-0000-0000-0000-000000000000	 
ERROR Exception: Could not load file or assembly 'Microsoft.Data.OData, Version=5.6.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35' or one of its dependencies. The system cannot find the file specified. 00000000-0000-0000-0000-000000000000	 
ERROR Failed to call GetTypes() 00000000-0000-0000-0000-000000000000	 
ERROR Exception: Could not load file or assembly 'Microsoft.Data.OData, Version=5.6.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35' or one of its dependencies. The system cannot find the file specified. 00000000-0000-0000-0000-000000000000	 
ERROR Failed to call GetTypes() 00000000-0000-0000-0000-000000000000	 
ERROR Exception: Could not load file or assembly 'Microsoft.Data.OData, Version=5.6.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35' or one of its dependencies. The system cannot find the file specified. 00000000-0000-0000-0000-000000000000	 

```

Kurulum öncesinde Prerequisites Installer başarıyla tüm bileşenleri yüklemiş görünse de, bu hatanın sebebi *Microsoft WCF Data Services 5.6* bileşeninin doğru bir şekilde yüklenememiş olması. [Bu](http://download.microsoft.com/download/1/C/A/1CAA41C7-88B9-42D6-9E11-3C655656DAB1/WcfDataServices.exe) linkten offline kurulum paketini indirip, Repair butonuna tıklayarak kurulumu onarabilirsiniz.

![wcf_data_services_56.png](https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2017/05/wcf_data_services_56.png)

Sunucuyu yeniden başlattıktan sonra Configuration Wizard başarıyla ilerleyecek.
