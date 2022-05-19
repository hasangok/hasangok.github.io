---
title: JavaScript Object to String
date: 2013-08-12 14:07
---

JavaScript'te ulaşmaya çalıştığım veriler Object olarak geldiği zaman, alert() ile görmeye çalıştığımda başarılı olamıyorum. Aslında almak istediğim veriyi almış oluyorum ama bunu görüntülemek için string türüne çevirmek gerekiyor. Aşağıdaki fonksiyonu buldum işime yarayan, object'in içinde ne var ne yok görebiliyoruz string'e dönüştürüp.

<!--more-->

```javascript
function objToString (obj) {
    var str = '';
    for (var p in obj) {
        if (obj.hasOwnProperty(p)) {
            str += p + '::' + obj[p] + '\n';
        }
    }
    return str;
}
```