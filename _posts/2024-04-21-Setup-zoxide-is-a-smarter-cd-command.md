---
title: Setup zoxide is a smarter cd command
author: bo3bdo
date: 2024-04-21 11:33:00 +0800
categories: [CMD]
tags: [CMD, zoxide, cd]
pin: false
image:
  path: https://raw.githubusercontent.com/ajeetdsouza/zoxide/main/contrib/tutorial.webp
---

## zoxide is a smarter cd command, inspired by z and autojump.

![img](https://raw.githubusercontent.com/ajeetdsouza/zoxide/main/contrib/tutorial.webp)

It remembers which directories you use most frequently, so you can "jump" to them in just a few keystrokes.

zoxide works on all major shells.

# Getting started

## Step 1 - Install

zoxide works with PowerShell, as well as shells running in Cygwin, Git Bash, and MSYS2.

The recommended way to install zoxide is via winget:

```powershell
winget install ajeetdsouza.zoxide
```

## Step 2 - Add to your shell

powershell
Add this to your configuration (the location is stored in $profile):

```powershell
notepad $PROFILE
```

if File not found, create it:

```powershell
New-Item -Path $PROFILE -Type File -Force
```

add this line to the file:

```powershell
Invoke-Expression (& {
    $hook = if ($PSVersionTable.PSVersion.Major -lt 6) { 'prompt' } else { 'pwd' }
    (zoxide init --hook $hook powershell) -join "`n"
})
```

## Cheat Sheet

zoxide is a smarter cd command for your terminal. It keeps track of the directories you visit, so that you can switch to them using just a few keystrokes.

![img](https://github.com/ajeetdsouza/zoxide/raw/main/contrib/tutorial.webp)

## Usage

```powershell
z foo       # cd to highest ranked directory matching foo
z foo bar   # cd to highest ranked directory matching foo and bar

z foo/      # can also cd into actual directories
z ..        # cd into parent directory
z -         # cd into previous directory

zi foo      # cd with interactive selection (requires fzf)
```
