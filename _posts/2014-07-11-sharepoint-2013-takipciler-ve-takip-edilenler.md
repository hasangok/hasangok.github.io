---
layout: post
title: SharePoint 2013 Takipçiler ve Takip Edilenler
date: 2014-07-11 01:53
author: hasangok
comments: true
Tags: [JavaScript, Sharepoint, SharePoint, Sosyal, takipçi]
---
*SharePoint 2013* ile bir sosyal portal geliştiriyorsak geçerli kullanıcıya ait takipçi / takip edilen bilgilerine Javascript Object Model ile ulaşmamız gerekebiliyor. Bunu Facebook ya da Twitter'da olduğu gibi, "***x yeni takipçi***" şeklinde bir bildirim mesajı ile bu takipçilerin kim olduklarını gösterecek bir arayüz geliştirebiliriz. Aşağıdaki örnek MSDN'de bulunsa da göz önünde bulunması için paylaşmak istedim.
Hepsinden önce, sayfamızda *SP.js* ve *SP.UserProfiles.js* dosyalarının sayfamıza eklenmiş olması gerekiyor. Bu kodların DOM yüklendikten sonra çalışmasını istediğimizden tabi ki *jQuery*'e de ihtiyacımız var.

```html
&lt;SharePoint:ScriptLink name="SP.js" runat="server" ondemand="false" localizable="false" loadafterui="true" /&gt; 
&lt;SharePoint:ScriptLink name="SP.UserProfiles.js" runat="server" ondemand="false" localizable="false" loadafterui="true" /&gt;
```

```javascript
var followed;
var followers;

$(document).ready(function () {
    SP.SOD.executeOrDelayUntilScriptLoaded(getFollowedAndFollowers, 'SP.UserProfiles.js');
});

function getFollowedAndFollowers() {
    var clientContext = SP.ClientContext.get_current();
    var followingManager = new SP.Social.SocialFollowingManager(clientContext);
    followers = followingManager.getFollowers();
    followed = followingManager.getFollowed(1);
    clientContext.executeQueryAsync(showFollowedAndFollowers, requestFailed)
}

function showFollowedAndFollowers() {
    var results = followed.length + 'kişiyi takip ediyorsunuz:\n';
    for (var i = 0; i &lt; followed.length; i++) {
        var user = followed[i];
        var name = user.get_name();
        var personalSiteUri = user.get_personalSiteUri();
        var pictureUri = user.get_imageUri();
        results += '\n' + name + '\n' + personalSiteUri + '\n' + pictureUri + '\n';
    }

    results += '\n' + followers.length + ' kişi sizi takip ediyor: \n';
    for (var i = 0; i &lt; followers.length; i++) {
        var user = followers[i];
        var name = user.get_name();
        var personalSiteUri = user.get_personalSiteUri();
        var pictureUri = user.get_imageUri();
        results += '\n' + name + '\n' + personalSiteUri + '\n' + pictureUri + '\n';
    }
    alert(results);
}

function requestFailed(sender, args) {
    $('#message').html('Error: ' + args.get_message());
}
```
