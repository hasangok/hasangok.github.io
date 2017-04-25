---
layout: post
title: SQL Server Tabloda Yapılan Değişiklikleri Kaydetmek
date: 2013-08-14 16:27
author: hasangok
comments: true
Tags: [Bilgisayar, SQL Server, Table Re-Creation, Veritabanı]
---
<p style="text-align: justify;">Daha önce çok kez başıma geldi, eminim sizin de başınıza gelmiştir. Bir projeye başlamadan önce kullanacağınız veritabanının tasarımını yaparsınız. Üzerinde ne kadar düşünseniz, ne kadar kafa patlatsanız da kodlama aşamasında illa ki bir eksiği çıkar ve yeni sütunlar, yeni ilişkiler eklemeniz gerekir. Bu durumda oluşturduğunuz tablolarınızda bir değişiklik yapmak istediğinizde SQL Server buna izin vermez ve veritabanının yeniden oluşturulması gerektiğini söyler. Bu durumun önüne geçmek ve yaptığınız değişiklikleri kaydedebilmek için:</p>

<ol style="text-align: justify;">
	<li><strong>Tools</strong> menüsünden <strong>Options</strong> seçilir.</li>
	<li><strong>Designers</strong> bölümüne geçilir.</li>
	<li>"<em>Prevent saving changes that require the table to be re-creation</em>" kutucuğunun işareti kaldırılır.</li>
</ol>
<p style="text-align: justify;"><img class="aligncenter size-full wp-image-185" alt="table-recreation" src="https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/08/table-recreation.png" width="644" height="375" /></p>
<p style="text-align: justify;">İstediğiniz değişiklikleri artık kaydedebilirsiniz ;)</p>
