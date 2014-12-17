---
layout: wiki
title: Kiosk Mode
wikiPageName: Kiosk-Mode
menu: wiki
---

During an experiment, subjects are expected to stay on the given pages/game, instead of browsing irrelevant websites or using other applications. Kiosk mode locks down the oTree pages on a web browser thus allows the subjects to focus. Here we provide some guidelines to initiate Kiosk mode with different browsers/on various systems. In general, Kiosk mode is rather user-friendly so one can easily search online how to use it on specific platforms.

#### iOS (iPhone/iPad)

1. Go to Setting – Accessibility – Guided Access
1. Turn on Guided Access and set a passcode for your Kiosk mode
1. Open your web browser and enter your URL
1. Triple-click home button to initiate Kiosk mode
1. Circle areas on the screen to disable (e.g. URL bar) and activate

#### Android

There are several apps for using Kiosk mode on Android, for instance: [Kiosk Browser Lockdown](https://play.google.com/store/apps/details?id=com.procoit.kioskbrowser&hl=en).

![](http://i.imgur.com/VJ72fKv.png)

For iOS and Android tablets, Kiosk mode will continue to function after normal restart. However, if subjects enter Android safe mode, the app can be disabled.

#### Chrome on PC
1. Go to Setting – Users – Add new user
1. Create a new user with a desktop shortcut
1. Right-click the shortcut and select “Properties”
1. In the “Target” filed, add to the end either ```--kiosk "http://www.your-otree-server.com"``` or ```--chrome-frame  --kiosk "http://www.your-otree-server.com"```
1. Disable hotkeys (see [here](http://superuser.com/questions/727072/what-windows-shortcuts-should-be-blocked-on-a-kiosk-mode-pc))
1. Open the shortcut to activate Kiosk mode

#### IE on PC
IE on PC
See [here](http://support2.microsoft.com/kb/154780)

#### Mac
There are several apps for using Kiosk mode on Mac, for instance: [eCrisper](http://ecrisper.com/). Mac keyboard shortcuts should be disabled.
