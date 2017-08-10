---
layout: post
author: David Boureau
minread: 8
title:  "How to write a Chrome extension"
date:   2017-06-06
categories: work
permalink: /blog/:title/
description: "How unit and integration test compares, and when to write them"
---

<p>&nbsp;</p>

The github repository is [here](https://github.com/bdavidxyz/basic_chrome_extension).

It is the most minimalistic, up-to-date tutorial to build your own plugin. It works as follow :

 - When you click on the plugin’s button, it outputs something in the Chrome Dev Tools console,
 - The JS is in a dedicated file.

## Steps

1. Create a directory “basic_chrome_extension” on your computer.
2. Inside, put the [3 files](https://github.com/bdavidxyz/basic_chrome_extension) "background.js", "content.js", and "manifest.json".
3. Open Chrome, and open url chrome://extensions.
4. Check checkbox named “developer mode”.
5. Click on button “Load unpacked extension…”.
6. Choose the directory “basic_chrome_extension”.
7. Good ! You should see a fresh, new, grey “B” icon next to the URL bar.
8. Open any decent website : github.com , (or twitter.com, or whatever :).
9. Open your chrome dev tools console : Press Ctrl+Shift+J (Windows / Linux) or Cmd+Opt+J (Mac).
10. Click on the “B” icon
11. Ta-da ! You should see “I'm content.js, man” in the console each time you press the magic “B” icon.

## Go further

 - [Chrome samples](https://developer.chrome.com/extensions/samples) 
 - [Official documentation](https://developer.chrome.com/extensions/overview)

