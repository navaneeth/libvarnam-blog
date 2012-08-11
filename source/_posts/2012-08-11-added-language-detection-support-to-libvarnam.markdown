---
layout: post
title: "Added language detection support to libvarnam"
date: 2012-08-11 15:42
comments: true
categories: [libvarnam, News, Features]
---
When using Varnam on web, you could possibly type words from multiple languages in the same editor. When a word is edited, Varnam needs to know the language of the word. `varnam_detect_lang()` API can be used to achieve this.

See it in action

```bash
$ ./varnamc -s ml --detect-language ಕನ್ನಡ
Kannada

$ ./varnamc -s ml --detect-language தமிழ்
Tamil

$ ./varnamc -s ml --detect-language हिन्दी
Hindi

$ ./varnamc -s ml --detect-language ଓଡ଼ିଆ
Oriya

$ ./varnamc -s ml --detect-language മലയാളം
Malayalam

```
Only few languages are supported currently. Adding support for more languages is easy and this method will work only for languages that follow Devanagari writing system.