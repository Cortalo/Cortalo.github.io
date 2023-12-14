---
title:  "IT Tips"
date:   2022-09-14 12:40:00 +0200
categories: cs
tags: shell
---

## Spacemacs

```
SPC w F # make-frame
SPC w o # other-frame
```

## Install Program Locally without sudo Permission

You need to compile these from source. It should just be a matter of

```
apt-get source PACKAGE # Or download the sourcecode release from github
./configure --prefix=$HOME
make
make install
```

## Conda

```
conda create -n envname python=3.9.7 ipython
conda acitvate envname
```

## PDFGREP

```
pdfgrep -in "pattern" *.pdf
# -i, --ignore-case
# -n, --page-number
```

The binary would then be located in `~/bin`.

## WSL Install Problem

- [wsl --install](https://docs.microsoft.com/en-us/windows/wsl/install) (double slash), then restart Windows.
- Sometimes Ubuntu can't be installed. It stucked at "Installing, this may take a few minutes".
- [Just hit ctrl+c](https://github.com/microsoft/WSL/issues/6405) to stop it.
- Try to open Ubuntu to see if it is successful.
- If not, [use wsl -l](https://docs.microsoft.com/en-us/windows/wsl/faq#how-do-i-uninstall-a-wsl-distribution-) to check if Ubuntu is installed or not.
- If it is not installed, uninstall Ubuntu in the Start Menu, then use `wsl --install -d Ubuntu` reinstall.

## Spacemacs Problem

- [Spacemacs fail to download the packages](https://github.com/syl20bnr/spacemacs/issues/8984)
- Use `emacs --insecure`

## Source Code Pro

Use [this-link](https://askubuntu.com/questions/193072/how-to-use-the-adobe-source-code-pro-font) to install Source Code Pro Font for Spacemacs.

## WSL GUI Blurry

Use [this-link](https://superuser.com/questions/1370361/blurry-fonts-on-using-windows-default-scaling-with-wsl-gui-applications-hidpi) to fix WSL GUI Blurry.

- It is okay to just change high DPI settings on the XLaunch shortcut.
- I don't need to change the variables like `GDK_SCALE` etc.

To [launch the server at start](https://superuser.com/questions/1372854/do-i-launch-the-app-xlaunch-for-every-login-to-use-gui-in-ubuntu-wsl-in-windows), put `config.xlaunch` in `Startup` folder.

test
