# Chrome Store Reviews

## Rejections

I have received quite a few random rejections and actually even a take down from my extension.

> "Spam and Placement in the Store"
> Items should work and provide some functionality upon installation.
> Items should provide the promised functionality that aligns with the description of the item.

This I got this one quite a few times, and after changing a description it actually took my extension off the web store.

I was able to get some information about the take down and learned that my application was breaking on install. My extension handled the error and spit out a id for the error. I use [Sentry](https://sentry.io). I found out that the [`topSites`](https://developer.chrome.com/extensions/topSites) api was disabled even though my manifest required it.
