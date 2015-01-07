---
layout: default
lang: en
title: Download
---
{% assign gura_version = '0.6.1' %}

# {{ page.title }}


## Packages

<table>

<tr>
<td>Windows Installer</td>
<td><a href="https://github.com/gura-lang/gura/releases/download/v{{ gura_version }}/gura-{{ gura_version }}-win32.msi"
  onClick="ga('send', 'event', 'download', 'click', 'gura-{{ gura_version }}-win32.msi');">gura-{{ gura_version }}-win32.msi</a></td>
</tr>
<tr>

<tr>
<td>Windows Binary</td>
<td><a href="https://github.com/gura-lang/gura/releases/download/v{{ gura_version }}/gura-{{ gura_version }}-win32.zip"
  onClick="ga('send', 'event', 'download', 'click', 'gura-{{ gura_version }}-win32.zip');">gura-{{ gura_version }}-win32.zip</a></td>
</tr>

<tr>
<td>MacOS Binary</td>
<td><a href="https://github.com/gura-lang/gura/releases/download/v{{ gura_version }}/gura-{{ gura_version }}.dmg"
  onClick="ga('send', 'event', 'download', 'click', 'gura-{{ gura_version }}.dmg');">gura-{{ gura_version }}.dmg</a></td>
</tr>

<tr>
<td>Sorce Package</td>
<td><a href="https://github.com/gura-lang/gura/releases/download/v{{ gura_version }}/gura-{{ gura_version }}-src.tar.gz"
  onClick="ga('send', 'event', 'download', 'click', 'gura-{{ gura_version }}-src.tar.gz');">gura-{{ gura_version }}-src.tar.gz</a></td>
</tr>

<!--
<tr>
<td style="padding-top: 3em">
<a href="http://www.softpedia.com/progClean/Gura-Clean-220177.html">
<img src="images/softpedia_free_award_f.gif" border="0" alt="100% FREE award granted by Softpedia" /></a></td>
</tr>
-->
</table>

[Release Notes](https://github.com/gura-lang/gura/releases)


## Install into Windows

It has been confirmed that Gura runs on the following versions of Windows.

* Windows 7
* Windows 8.1

Launch the installer
<a href="https://github.com/gura-lang/gura/releases/download/v{{ gura_version }}/gura-{{ gura_version }}-win32.msi"
  onClick="ga('send', 'event', 'download', 'click', 'gura-{{ gura_version }}-win32.msi');">gura-{{ gura_version }}-win32.msi</a>,
which will install necessary files and register file extensions `.gura`, `.guraw`, `.gurc` and `.gurcw` as executable ones.

If you don't want to modify registry, you can just expand ZIP file
<a href="https://github.com/gura-lang/gura/releases/download/v{{ gura_version }}/gura-{{ gura_version }}-win32.zip"
  onClick="ga('send', 'event', 'download', 'click', 'gura-{{ gura_version }}-win32.zip');">gura-{{ gura_version }}-win32.zip</a>
  in some directory and edit PATH environment so that it includes `gura\bin-x86` directory in the expanded content.

## Install into MacOS

It has been confirmed that Gura runs on the following versions of MacOS.

* OS X 10.9 Mavericks

Open disk image file
<a href="https://github.com/gura-lang/gura/releases/download/v{{ gura_version }}/gura-{{ gura_version }}.dmg"
  onClick="ga('send', 'event', 'download', 'click', 'gura-{{ gura_version }}.dmg');">gura-{{ gura_version }}.dmg</a>
and drag `Gura.app` icon to `Applications` folder.

**You can't use Launchpad to run `Gura.app`** as it'll be blocked by Gatekeeper.
This is because Gura hasn't been shipped with an Apple Developer ID so far.
Instead, browse the application in **Finder** and do "Open" in right-click menu.

Launching `Gura.app` will open a Terminal with Gura command prompt
in which you can evaluate Gura scripts interactively.
If you want to write and execute a Gura script file,
call `setup()` function in the prompt to create a symbolic link `/usr/bin/gura`
that allows you to execute the interpreter from anywhere in the system.

## Install into Linux

It has been confirmed that Gura runs on the following distributions of Linux.

* Ubuntu 13.10
* Ubuntu 14.04
* Xubuntu 14.04
* lubuntu 14.04
* Fedora 20 (`wx` modules doesn't work well)

In default configuration, Ubuntu and Fedora do not include C++ compilers, cmake utility and readline library.
Install them as below before building Gura.

For Ubuntu:

    $ sudo apt-get install build-essential cmake libreadline-dev rpm

For Fedora:

    # yum install gcc gcc-c++ make cmake readline-devel

Download a source package
<a href="https://github.com/gura-lang/gura/releases/download/v{{ gura_version }}/gura-{{ gura_version }}-src.tar.gz"
  onClick="ga('send', 'event', 'download', 'click', 'gura-{{ gura_version }}-src.tar.gz');">gura-{{ gura_version }}-src.tar.gz</a>.
Then, follow the steps below to build Gura executables and modules.

    $ tar xvfz gura-{{ gura_version }}.tar.gz
    $ cd gura-{{ gura_version }}
    $ mkdir build
    $ cd build
    $ ../configure
    $ make
    $ sudo ./setup-guest
    $ ./build-modules

After that, follow the steps below to install them to the system.

    $ sudo make install
    $ sudo ldconfig     # necessary only for the first install
