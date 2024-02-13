---
title: PowerShell Prompt with Oh My Posh and the Windows Terminal
author: bo3bdo
date: 2024-02-03 11:33:00 +0800
categories: [Windows, PowerShell]
tags: [powershell, oh-my-posh, windows-terminal]
pin: false
image:
  path: assets/img/image_9f793bcd-61f2-424b-845b-46b63b2f37eb.png
---

## Let's get you set up!

## GET POWERSHELL

Open a PowerShell prompt and run the following command:

```powershell
winget install JanDeDobbeleer.OhMyPosh -s winget
```

Now that Oh My Posh is installed, you can go ahead and configure your terminal and shell to get the prompt to look exactly like you want.

## Next steps :

1. install a font that supports the [`Nerd Fonts`](https://ohmyposh.dev/docs/installation/fonts)
2. install a theme from the [gallery](https://ohmyposh.dev/docs/installation/themes)
3. configure your terminal and shell to use the new font and theme

## Change your prompt

Edit your PowerShell profile script, you can find its location under the $PROFILE variable in your preferred PowerShell version. For example, using notepad:

```powershell
New-Item -Path $PROFILE -Type File -Force
```

```powershell
notepad $PROFILE
```

```powershell
oh-my-posh init pwsh | Invoke-Expression
```

## TURN YOUR POWERSHELL DIRECTORIES UP TO 11 WITH TERMINAL-ICONS

Is your prompt not extra enough? That's because your directory listing needs color AND cool icons!

```powershell
Install-Module -Name Terminal-Icons -Repository PSGallery
```

```powershell
Import-Module -Name Terminal-Icons
```

Now, open your PowerShell

![alt text](../assets/img/image_9a01061f-23d8-4ca9-8ee9-2b28d358ddd7.png)
