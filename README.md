# Learn How to Build Chrome Extensions

## Why?

Chrome Extensions are a *whole other* ***world of opportunity***
to build web-enabled tools!


## What?

Almost ***53% of people*** use Chrome to access the Internet on desktop devices.
see: http://gs.statcounter.com/#desktop-browser-ww-monthly-201506-201506-bar
Chromebooks are the fastest growing segment of the PC market.
In 2014 Chromebooks accounted for 14 percent of all laptop sales for both
the commercial and retail channels; up 85 percent from 2013.
http://betanews.com/2015/02/24/2015-is-year-of-the-chromebook/

Chrome Extensions (*or "Apps"*) allow you to create in-browser tools
which add functionality to the browsing experience.
In our case we want to let the person

## *How*?


## Permissions

+ What are the permissions? https://developer.chrome.com/extensions/permissions


## *Examples*

### Browser Action (When the person clicks on the Extension Icon)

Browser Actions allow you to add an icon to the browser e.g:
![browser action](https://developer.chrome.com/static/images/browser-action.png)
See: https://developer.chrome.com/extensions/browserAction

Example of a simple Browser Action is an icon which, when clicked
alters the page background.
See: examples/make_page_red

### Display list of Bookmarks

Uses the bookmarks API to show a list of the person's bookmarks
when they click on the icon (`browser_action`)

![chrome-extension-bookmarks-viewer](https://cloud.githubusercontent.com/assets/194400/11568030/e4a1eba8-99e1-11e5-83a3-cf7709a10ed0.png)

See: examples/my_bookmarks

### Change the `src` of Icon when clicked

Imagine your app wants to change the icon in response to an event or a notification:
That's quite easy with the following line:
```js
chrome.browserAction.setIcon({path:"icon-notification.png"});
```

see: examples/set_icon_path

### Access Browser Data (*Delete History*)

Use the `chrome.browsingData` API to remove browsing data from a user's local profile.

![browsingdata_api](https://cloud.githubusercontent.com/assets/194400/11569180/62dc7956-99e8-11e5-8c1c-15be80af7590.png)

The API only allows you to `erase` history, so its only useful for a *limited*
set of applications.

see: https://developer.chrome.com/extensions/browsingData

### Using Keyboad Shortcuts in your Extensions

Using the `commands.onCommand` we can issue keyboard commands to trigger events in our extension.

The commands are defined in the `manifest.json` file as:

```js
"commands": {
  "toggle-feature": {
    "suggested_key": { "default": "Ctrl+Shift+Y" },
    "description": "Send a 'toggle-feature' event to the extension"
  },
  "_execute_browser_action": {
    "suggested_key": {
      "default": "Ctrl+Shift+F",
      "mac": "MacCtrl+Shift+F"
    }
  }
}
```
This can be useful for opening a background page (popup) to read content,
e.g: imaging if your extension provided an instant messaging facility
and you could see the latest messages from any page without needing
to have the messenger open.

see: https://developer.chrome.com/extensions/commands

### Using desktopCapture to Get a Snapshot of the Screen

`desktopCapture` allows you to capture the client's screen.

![chrome-extension-capture-desktop](https://cloud.githubusercontent.com/assets/194400/11576119/7f2aa1ae-9a0c-11e5-8f61-f342b5f60448.png)

see: examples/desktop_capture
and: https://developer.chrome.com/extensions/desktopCapture

<br />
<br />

## Questions?

**Q**: Can we have ***both*** `page_action` ***and*** `browser_action` ?  
**A**: No. But you can create multiple extensions and have them inter-communicate
see: http://stackoverflow.com/questions/14519458/google-chrome-extension-browser-page-action
and: https://developer.chrome.com/extensions/extension#event-onMessageExternal

**Q**: How can we check when the Tab/Page has finished loading?  
**A**: Add an event listener:
```js
chrome.tabs.onUpdated.addListener(function(tabId , info) {
    if (info.status == "complete") {
        // your code ...
    }
});
```
http://stackoverflow.com/questions/2149917/chrome-extensions-how-to-know-when-a-tab-has-finished-loading-from-the-backgr

## Background Reading / Watching


### Videos

+ Google Chrome Extensions: How to build an extension
(Google Developers official):
https://www.youtube.com/watch?v=e3McMaHvlBY
(from 2009 but all the info is still valid)
+ Building Your First Chrome Extension:
https://www.youtube.com/watch?v=pT-b2SpFIWo

### Guides

+ Getting Started: Building a Chrome Extension:
https://developer.chrome.com/extensions/getstarted
+ How to Create a Chrome Extension in 10 Minutes Flat:
http://www.sitepoint.com/create-chrome-extension-10-minutes-flat/
+ How to Build a Chrome Extension:
http://lifehacker.com/5857721/how-to-build-a-chrome-extension
+ Developing Google Chrome Extensions:
http://code.tutsplus.com/tutorials/developing-google-chrome-extensions--net-33076
+ Publishing Your App: https://developer.chrome.com/webstore/publish

### Articles

+ Everything You Need To Know About Browser Extensions:
http://www.howtogeek.com/169080/beginner-geek-everything-you-need-to-know-about-browser-extensions/
+ What percentage of Internet users use browser extensions?
https://www.quora.com/What-percentage-of-Internet-users-use-browser-extensions
in 2010 33% of Chrome Users had extensions.
I was unable to find more recent data...
(please update if you find recent stats)
+ Publishing a Chrome Extension? 7 Tips to Get More Downloads:
http://ecquire.com/blog/how-to-get-more-chrome-extension-downloads/
+ Your Chrome Extensions May Be Stealing Your Personal Info: Here's How to Stop Them:
http://digiwonk.wonderhowto.com/how-to/your-chrome-extensions-may-be-stealing-your-personal-info-heres-stop-them-0150766/
(*Privacy ... the reason I don't use any extensions...*)
+ Warning: Your Browser Extensions Are Spying On You:
http://www.howtogeek.com/180175/warning-your-browser-extensions-are-spying-on-you/
+ Google Chrome Privacy Whitepaper:
https://www.google.co.uk/chrome/browser/privacy/whitepaper.html
+ So you want to build a chrome extension:
https://blog.hartleybrody.com/chrome-extension/ (*BuzzKill example* by @hartleybrody)
+ What are Chrome Apps? https://developer.chrome.com/apps/about_apps (*they're awesome*!)
