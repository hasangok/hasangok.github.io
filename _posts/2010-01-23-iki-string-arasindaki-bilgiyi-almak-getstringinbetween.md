---
title: İki string arasındaki bilgiyi almak (GetStringInBetween)
date: 2010-01-23 17:19
---

Bir web sayfasında belli HTML etiketleri arasındaki bir bölümü, ya da elinizdeki herhangi metnin belli bir bölümünü seçip almak isteyebilirsiniz. Örneğin web siteniz için yazdığınız programın başlığını, sitenizden almak istediniz. Ne yapmanız gerekir? Tabi ki, sayfanızdaki &lt;title&gt; ve &lt;/title&gt; arasındaki bilgiye ulaşmanız...

<!--more-->
![csharp_logo](/uploads/2009/10/csharp_logo.gif)  
İşte ben de, C# ile HTML kodları arasında gezinip "Böyle bir şeyi nasıl yapabilirim?" sorusuna cevap ararken, küçük bir araştırma sonucu elde ettiğim harika bir metodu paylaşacağım sizlerle: GetStringInBetween...

Bir metindeki belli bir bölüme ya da belli HTML etiketleri arasındaki bilgiye ulaşmak GetStringInBetween ile oldukça basitleşiyor. Öncelikle programınıza eklemeniz gereken metodun kodlarına göz atalım:

```csharp
public static string[] GetStringInBetween(string strBegin, string strEnd, string strSource, bool includeBegin, bool includeEnd)
{
    string[] result = { "", "" };
    int iIndexOfBegin = strSource.IndexOf(strBegin);
    if (iIndexOfBegin != -1)
    {
        // include the Begin string if desired 
        if (includeBegin)
            iIndexOfBegin -= strBegin.Length;
        strSource = strSource.Substring(iIndexOfBegin + strBegin.Length);
        int iEnd = strSource.IndexOf(strEnd);
        if (iEnd != -1)
        {
            // include the End string if desired 
            if (includeEnd)
                iEnd += strEnd.Length;
            result[0] = strSource.Substring(0, iEnd);
            // advance beyond this segment 
            if (iEnd + strEnd.Length &lt; strSource.Length)
                result[1] = strSource.Substring(iEnd + strEnd.Length);
        }
    }
    else
        // stay where we are 
        result[1] = strSource;
    return result;
}
```
Kullanımına bakacak olursak:
```csharp
string myString = "&lt;title&gt;Hasan Gök v0.5b | Karalama Defteri&lt;/title&gt;";
string [] result = GetStringInBetween("&lt;title&gt;", "&lt;/title&gt;", myString, false, false);
string output = result[0];
string next = result[1];
```
Burada result[0], bize tam olarak istediğimiz bölümdeki stringi veriyor (yukarıdaki örnek için title etiketleri arasında kalan yer, yani sitenin başlığı). result[1] ise, metnin geri kalanını saklıyor (Örneğin başlıktan sonra &lt;body&gt;&lt;/body&gt; arasındaki bilgiyi almak isterseniz, GetStringInBetween("&lt;body&gt;", "&lt;/body&gt;", result[1], false, false);  kullanabilirsiniz).

Buradaki "false" ifadeleri de, ilk koddan da anlayacağınız üzere, başlangıç ve bitiş stringlerini de alıp almayacağınızı belirliyor. Başlığımızı alırken false yerine true kullanmış olsaydık result[0], title etiketlerini de içerecekti.

Kodun gerçekten başarılı çalıştığına canlı bir örnek olması için, [buradan indirip bakabileceğiniz](/dosyalar/BaslikOkuyucu.zip) 2 satırlık bir program hazırladım (çalışması için .NET Framework gerekir). Girdiğiniz herhangi bir web adresinin başlığını size gösteriyor 🙂

Ben burada yazıma son veriyorum...  
Aklınıza takılan bir şey olursa aşağıya yorum bırakabilirsiniz 😉  
Sevgiyle kalın, görüşmek üzere...
