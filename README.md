# ray-peat-styled

The primary purpose of this extension is to fix a longstanding issue preventing [raypeat.com](https://raypeat.com) from loading its stylesheet. (Yes, it is meant to look different.) The issue is, despite having SSL configured, there are still some `http` requests, and modern browsers block mixed content.

Dr. Peat passed more than a year ago, and it's likely his website wasn't looked at for a long while before then, hence the existence of this extension to help out.

If you poke around dev tools, you can see four blocked `http` requests. The first is the stylesheet, `raypeat.css`, which this extension loads. The second, `nav-collapse.js,` is some very old and presumably dysfunctional javascript. The third and fourth are a javascript and css file from Google, `jsapi.js` and `default.css`; the former is accessible but unreadable, the latter 404s. The two javascript files are included in the `/archived` folder of this repository, but are not used in the extension. I took the liberty of appending a rule to `raypeat.css` to hide the "Loading" text that waits for the blocked JS.

## Usage

You can install the extension from the [Chrome Web Store](https://chrome.google.com/webstore/detail/ray-peat-styled/lmmdaaknmobjkebncemnchleoimfjnkp). Or, if you aren't using a chromium-based browser, you can download the latest release and manually add install it.

## Future

I would like to try loading the javascript files just to see what happens, either by injecting the scripts or intercepting the http requests and making them https. I might be able to recreate the functionality of `nav-collapse.js` with some effort. If I do this and something interesting happens, I would update the extension with the injection method. I want to avoid *actually fixing* the requests, because that means more network traffic for whoever is still paying the bill to keep raypeat.com on the internet.

On that topic, it doesn't look like the website uses the cache. Considering how lightweight the site is, practically everything could be saved in the extension.

Lastly, the "footer" block located beneath "Links" on the sidebar is probably meant to be glued to the bottom of the screen. I think it looks okay as is.