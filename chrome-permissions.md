# Chrome permissions

With an enterprise account companies can disable permissions on a Chrome extension even if that Chrome extension ask for the permission by default. This means that every Chrome api should be treated as a conditional even if the permission is granted on installation.

This was something I found out after my Chrome extension kept failing [Store Review](./chrome-store-reviews) because of the enterprise policy at Google.

The implication of this is that any time you are using a Chrome web api you should first check the permissions.

```javascript
chrome.permissions.contains({ permissions: ['topSites'] }, (hasPerimssion) => {
  if (hasPermission) chrome.topSites.get(callback)
})
```

This is something that could probably be filled by abstraction to check these values before using the api.

```javascript
extension.topSites.get = (callback) => {
  chrome.permissions.contains({ permissions: ['topSites'] }, (hasPermssion) => {
    if (hasPermssion) {
      chrome.topSites.get(callback)
    } else {
      callback(fallbackSites)
    }
  })
}
```
