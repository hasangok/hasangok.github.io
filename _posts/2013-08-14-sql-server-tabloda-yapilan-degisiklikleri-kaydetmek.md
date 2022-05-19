---
title: SQL Server Tabloda Yapılan Değişiklikleri Kaydetmek
date: 2013-08-14 16:27
---

Daha önce çok kez başıma geldi, eminim sizin de başınıza gelmiştir. Bir projeye başlamadan önce kullanacağınız veritabanının tasarımını yaparsınız. Üzerinde ne kadar düşünseniz, ne kadar kafa patlatsanız da kodlama aşamasında illa ki bir eksiği çıkar ve yeni sütunlar, yeni ilişkiler eklemeniz gerekir. Bu durumda oluşturduğunuz tablolarınızda bir değişiklik yapmak istediğinizde SQL Server buna izin vermez ve veritabanının yeniden oluşturulması gerektiğini söyler. Bu durumun önüne geçmek ve yaptığınız değişiklikleri kaydedebilmek için:

<!--more-->
1. **Tools** menüsünden **Options** seçilir.
2. **Designers** bölümüne geçilir.
3. "*Prevent saving changes that require the table to be re-creation*" kutucuğunun işareti kaldırılır.

![table-recreation](/uploads/2013/08/table-recreation.png)

İstediğiniz değişiklikleri artık kaydedebilirsiniz 😉