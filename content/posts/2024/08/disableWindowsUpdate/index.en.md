---
title: "How to Disable Windows Update and Debloat Windows"
date: 2024-08-29T07:31:43+07:00
lastmod: 2025-12-16T09:23:43+07:00
tags: [Casual]
categories: [Posts]
slug: tweakWindows
thumbnailLink: "https://media.rafliard.net/content/posts/2024/08/09_disableWindowsUpdate/blockWindowsUpdate.webp"
draft: false
excludeFromSearch: false
summary: "Simple guide to enable/disable Windows Update as easy as run a program. Also include how to debloat windows by yourself!"
---

{{< figure
    src="https://media.rafliard.net/content/posts/2024/08/09_disableWindowsUpdate/blockWindowsUpdate.webp"
    class="xl:grid-w50"
    >}}

Every single days, Windows 11 becomes buggier and huge mess. Personally I only use Windows 11 in my office laptop as standard issue device and some tools (for electronics) that I use stuck on Windows. Due to Windows 10 being End of Service last October, everyone have to migrate into Windows 11 especially those among office user.

Without further ado, let's move to the topic.

## How to Turn Off Windows Update (Reversible)

I use the one from tsgrgo which reliable for me and some of my clients. We can also read the guide listed on the repo.

{{< github repo="tsgrgo/windows-update-disabler" showThumbnail=false >}}

### 1. Clone repo using `git clone` or download main as Zip

### 2. Extract `windows-update-disabler-main.zip`

### 3. Run `disable updates.bat` to disable Windows Update service

### 4. To enable Windows Update, we can run `enable updates.bat`

<hr>

## How to Debloat Windows

Few utilities that I used to rock on has been archived due to Windows 10 End of Service as these utilities mostly build around Windows 10 but also works in Windows 11. Therefore I had to use Chris Titus's script which can be accessed here

{{< github repo="ChrisTitusTech/winutil" showThumbnail=false >}}

### 1. Run PowerShell or Terminal as Administrator

### 2. Paste this line into Powershell/Terminal

```bash
irm "https://christitus.com/win" | iex
```

### 3. Read the Documentation for what can be remove and what not

[For Further information, you can read documentation section of the repo.](https://github.com/ChrisTitusTech/winutil?tab=readme-ov-file#-documentation)

It's all easy as long as you read the instruction. RTFM!🔥