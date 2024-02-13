---
title: Setup PHP CS Fixer in VSCode (junstyle php-cs-fixer)
author: bo3bdo
date: 2024-02-10 11:33:00 +0800
categories: [VSCode]
tags: [VSCode, PHP-CS-Fixer, PHP]
pin: false
image:
  path: /assets/img/filament-slugs-featured.webp
---

# php-cs-fixer
PHP-CS-Fixer is a command line tool that formats PHP files, ensuring they follow certain code style standards.

The VSCode extension php cs fixer by junstyle integrates PHP-CS-Fixer into VSCode.

This guide will cover the configs you need to set to get php cs fixer by junstyle working in VSCode.

# Step 1 - Install
If you haven’t already, install the extension php cs 
[fixer by junstyle](https://marketplace.visualstudio.com/items?itemName=junstyle.php-cs-fixer)

# Step 2 - Configure

Next, open your VSCode settings.json file:

- View > Command Palette
- Type in settings and choose **Preferences: Open User Settings (JSON)**
In your settings add these configs:

```json
{
  "php-cs-fixer.executablePath": "${extensionPath}/php-cs-fixer.phar",
  "php-cs-fixer.onsave": true,
  "php-cs-fixer.formatHtml": true,
  "[php]": {
    "editor.defaultFormatter": "junstyle.php-cs-fixer"
  },
}
```

To test things out, we can create a file called test.php with some unformatted code:

```php
<?php function hi(){echo 'hi';}
```
Upon saving this file, you should see the formatting gets cleaned up to:

```php
<?php

function hi()
{
    echo 'hi';
}
```

## Troubleshooting

If the formatter doesn’t work, you might see an error pop up that says:

PHP CS Fixer: executablePath not found. Try setting "php-cs-fixer.executablePath": "${extensionPath}/php-cs-fixer.phar" and try again.

This error message suggests you don’t have the setting php-cs-fixer.executablePath set, but we know we do as we completed that in the above steps.

Another reason, then, of why we might see this message is because VSCode can’t locate an install of PHP on your system in order to execute the php cs fixer program.

To confirm this, try running the command which php in a bash-based command line program. If it reports back that the command is not found, that’s your problem.



![phoho](https://s3.amazonaws.com/making-the-internet/php-command-not-found@2x.png)


To resolve the issue, you need to set up PHP on your computer. There are many ways to do this, but I suggest the following programs that include PHP:

Once you have one of those programs installed, you need to update your VSCode settings telling it where it can find the PHP executable that came with the program. Here are some examples:

Mac with PHP via Herd (Update YourUsername with your username):

```json
"php.validate.executablePath": "/Users/YourUsername/Library/Application Support/Herd/bin/php"
```

Windows with PHP via WSL (Update YourUsername with your username):

```json
"php.validate.executablePath": "c:/laragon/bin/php/php-8.1.10-Win32-vs16-x64/php.exe",
```


[![IMAGE ALT TEXT HERE](http://img.youtube.com/vi/I1gugtGN07Y/0.jpg)](http://www.youtube.com/watch?v=I1gugtGN07Y)

## Optional: Make PHP globally available
The above setting will make it so that VSCode can find PHP on your system, but PHP might still not be available in command line. To make PHP globally available, update your computer’s PATH variable adding one of the above paths so the php command is available globally on your computer. Once you do that, you don’t have to make specific setting changes in VSCode to tell it where PHP is. For instructions on updating your PATH variable, check out one of the following guides:
