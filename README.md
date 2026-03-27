# What’s changed:
This fork updates the extension to support the new Microsoft Teams web domain `https://teams.cloud.microsoft/*`. The original version only matched `teams.live.com` and `teams.microsoft.com`, so it did not run on the new Teams URL and presence would still go “Away”.  
  
Notes:
- No behavior changes other than adding the new host match.  
- Tested with Teams PWA and web client in Chrome; extension now keeps status active as expected on `teams.cloud.microsoft`.
- This fork currently targets Google Chrome / Chromium only. The original extension also shipped a Firefox .xpi, but that is not maintained here.


# Keep Teams Awake

Keep Teams Awake is a very simple, barebones "mouse jiggler" browser extension for Microsoft Teams.

It works on Firefox and Chrome-based browsers.

### The problem

The web version of Microsoft Teams can't (and shouldn't!) track mouse or keyboard behavior unless it has focus.

This means that if you have a different browser tab/window open, or you are using a different program on your computer, then Teams will not be in focus, and it will not see any of your mouse or keyboard interactions.

This is good for privacy and security reasons, but it does present a problem: Teams will assume that you aren't using your computer.

Teams will then automatically set your status to "Away", making other people mistakenly think that you aren't available, and will also result in Teams not checking for new messages as regularly as it should.

This problem has become more apparent as Microsoft has shifted away from native desktop apps for some platforms (eg. Linux) and replaced the native apps with web versions, leaving those users with broken "Away" functionality.

### The solution

This browser extension sends fake mouse movement events to the Teams website at regular intervals to ensure that Teams remains active.

These aren't real mouse movement events. So your mouse won't move, but the website will think that it did.

Also, since they aren't real mouse movement events, it will work even if Teams isn't in the active browser tab, if it's on a different workspace/virtual desktop, and so on.

## Install

### Direct Download

Download the [latest release](https://github.com/junderw52/keep-teams-awake/releases/latest) from GitHub.

Download the chrome.zip file, then go to the Chrome extensions page by either:

- entering chrome://extensions in your address bar
- clicking on the Extensions icon to the right side of your address bar and clicking on Manage Extensions, or 
- opening the browser menu and going to Settings -> Extensions

From the extensions page, enable Developer Mode by ticking the checkbox in the upper-right corner.

Then drag and drop the chrome.zip file onto the web page to install it.

### From Source

Follow the steps above to enable Developer Mode and go to the Manage Extensions page.

Clone this repository, or download the latest source code zip and extract it.

Then click on the "Load Unpacked" button and select the `src` directory in the downloaded source code.

That will tell Chrome to install the content in the `src` directory as a browser extension.
