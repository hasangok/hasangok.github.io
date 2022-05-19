---
title: Google'dan Programlama Dili - Go!
date: 2009-11-25 03:52
---

Bir adım daha... Google bu kez bambaşka bir alana el attı ve kendi geliştirdiği programlama dilini duyurdu! Bu yeni programlama dilinin adı "***Go***".

<!--more-->
![go-logo](/uploads/2009/11/go-logo.png)  
Chip dergisinin sitesinde bu dil için "***Go**, özellikle çok işlemcili sistemler için uygulama geliştirmeye elverişli olacak ve nesne odaklı tasarım için sade bir başlangıç sunacak.*" denmiş. Dilin ana sayfalarında ne denmiş onun Türkçesini de dilim döndüğünce sizlerle paylaşayım. Bakalım Google bu dili nasıl tanımlıyor:

### ***Go...***  
### ...basittir
```go
package main
import "fmt"
func main() {
  fmt.Printf("Merhaba ziyaretci\n")
}
```
### ...hızlıdır  
Go derleyicileri  kodları hızlıca derler. Tipik derlemeler saniyeden daha kısa sürede tamamlanır, programlar C ve C++ kodları kadar hızlı çalışır.

### ...güvenlidir  
Go'da tip güvenliği ve bellek güvenliği vardır. İşaretçiler vardır ama işaretçi aritmetiği yoktur. Rastgele erişim için aralıkları belli dilimler kullanılır.

### ...eşzamanlıdır  
Go, sistemleri ve sunucuları "küçük iletişim paketleri" olarak yazmanızı destekler. (Goroutines olarak ifade edilmiştir ve dilde güçlü bir şekilde desteklenmiştir.) İsterseniz binlerce goroutine çalıştabilir, yığın taşmalarına elveda diyebilirsiniz.

### ...eğlencelidir  
Go kodları hızlıca derler, temiz bir grameri, çöp toplama (garbage collection) mekanizması, her tür için metodları ve run-time reflection vardır. Dinamik bir dilfir ama statik bir dil kadar hzılı ve güvenlidir. Kullanması eğlencelidir.

### ... açık kaynaklıdır  
Bunlar Go dili sitesinin ana sayfasında yer alan ifadeler (birebir çeviri değildir). Dil hakkında daha kapsamlı bilgi için http://golang.org adresini ziyaret etmenizde fayda var. Ama yazıyı bitirmeden, bir programlama klasiği "***Merhaba Dünya!***" programını sizlerle paylaşmak istiyorum:
```go
package main
import fmt "fmt"  // Package implementing formatted I/O.
func main() {
fmt.Printf("Merhaba dunya\n");
}
```
Yeni bir dile yine, yeniden "Merhaba!" dedik. Bir bilgisayar mühendisi adayı olarak, altında Google imzası olan bu dil ile de ilgilenmek, en azından fikir sahibi olmak boynumuzun borcu diye düşünüyorum. Yaza bir uğraş daha çıktı işte, hayırlısı 🙂

Bir sonraki yazıya dek, kendinize iyi bakın...
