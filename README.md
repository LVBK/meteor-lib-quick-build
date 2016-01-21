How to get meteor-lib

run: meteor build --directory build-version

check builded js file in web.brower and remove some line
Add to the top of find
```javascript
ServiceConfiguration_Static = {};
ServiceConfiguration_Static.configurations={
    service: 'facebook',
    appId: '12345678901234567890',
    secret: 'secret12345678901234567890'
};
```
Replace
```javascript
Package["service-configuration"].ServiceConfiguration
```
1st you can find
by
```javascript
ServiceConfiguration_Static
```

Remove 1 if you can find it.

```javascript
!function(){var e=Package.meteor.Meteor;(function(){angular.module("angular-meteor").config(["$provide",function(e){var t=["html","tpl","tmpl","template","view"];e.decorator("$templateCache",["$delegate",function(e){var a=e.get;return e.get=function(e){var r=a(e);if(angular.isUndefined(r)){var n=((e.split(".")||[]).pop()||"").toLowerCase();if(t.indexOf(n)>-1)throw new Error("[angular-meteor][err][404] "+e+" - HTML template does not exists!")}return r},e}])}])}).call(this),"undefined"==typeof Package&&(Package={}),Package["angular-templates"]={}}();
.........
```


Remove 2 if you can find it.

```javascript
!function(){var e=Package.meteor.Meteor,t=Package.tracker.Tracker,n=Package.tracker.Deps,a=Package.retry.Retry,r=Package["ddp-client"].DDP,o=Package.mongo.Mongo,i=Package.underscore._,s,c;(function(){var t=__meteor_runtime_config__.autoupdateVersion||"unknown",n=__meteor_runtime_config__.autoupdateVersionRefreshable||"unknown";s=new o.Collection("meteor_autoupdate_clientVersions"),c={},c.newClientAvailable=function(){return!!s.findOne({_id:"version",version:{$ne:t}})||!!s.findOne({_id:"version-refreshable",version:{$ne:n}})},c._ClientVersions=s;var r=!1,u=new a({minCount:0,baseTimeout:3e4}),l=0;c._retrySubscription=function(){e.subscribe("meteor_autoupdate_clientVersions",{onError:function(t){e._debug("autoupdate subscription failed:",t),l++,u.retryLater(l,function(){c._retrySubscription()})},onReady:function(){if(Package.reload)var a=function(a){var s=this;if("version-refreshable"===a._id&&a.version!==n){n=a.version;var c=a.assets&&a.assets.allCss||[],u=[];i.each(document.getElementsByTagName("link"),function(e){"__meteor-css__"===e.className&&u.push(e)});var l=function(t,n){var a=i.once(n);if(t.onload=function(){r=!0,a()},!r)var o=e.setInterval(function(){t.sheet&&(a(),e.clearInterval(o))},50)},d=i.after(c.length,function(){i.each(u,function(e){e.parentNode.removeChild(e)})}),_=function(t){document.getElementsByTagName("head").item(0).appendChild(t),l(t,function(){e.setTimeout(d,200)})};0!==c.length?i.each(c,function(t){var n=document.createElement("link");n.setAttribute("rel","stylesheet"),n.setAttribute("type","text/css"),n.setAttribute("class","__meteor-css__"),n.setAttribute("href",e._relativeToSiteRootUrl(t.url)),_(n)}):d()}else"version"===a._id&&a.version!==t&&(o&&o.stop(),Package.reload&&Package.reload.Reload._reload())},o=s.find().observe({added:a,changed:a})}})},c._retrySubscription()}).call(this),"undefined"==typeof Package&&(Package={}),Package.autoupdate={Autoupdate:c}}();
```

Remove 3 if you can find it.


```javascript
Autoupdate=Package.autoupdate.Autoupdate,
```
Note: sometime with update of Meteor, something will change. Please keep observe and find something like that to delete or modify.