---
title: Web Partta Full Control Yetkisi
date: 2013-08-19 15:19
---

Yazdığımız web partlarda bazı kodların tam denetim yetkisiyle çalışmasını isteyebiliyoruz. Benim için bu ihtiyaç *User Profile*'dan bilgi çekip, kişilerin doğum günlerini göstermek istediğimde ortaya çıkmıştı. **Full Control** -*Tam Denetim*- yetkisiyle çalıştırmak istediğimiz kod kısımlarını aşağıdaki metod içerisine yazarsak işimiz görülmüş oluyor:

<!--more-->
```csharp
SPSecurity.RunWithElevatedPrivileges(delegate()
{
	//Tam denetim yetkisi ile
	//çalışacak kodlar
});
```

**Not:** Sandbox projelerde "***RunWithElevatedPrivileges***" metodunun kullanılamayacağını da belirteyim.
