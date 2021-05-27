![dopameme](dopameme.full.png)

# dopameme

dopameme is an audio player which tries to make organizing and listening to music as simple and pretty as possible. This version is written using Electron, Angular and Typescript. The original dopameme (for Windows), which is written in WPF and C#, remains available <a href="https://github.com/digimezzo/dopameme-windows">here</a>.

dopameme icons created by <a href="https://www.itssharl.ee/">Sharlee</a>.

[![Release](https://img.shields.io/github/release/digimezzo/dopameme.svg?style=flat-square)](https://github.com/digimezzo/dopameme/releases/latest)
[![Issues](https://img.shields.io/github/issues/digimezzo/dopameme.svg?style=flat-square)](https://github.com/digimezzo/dopameme/issues)
[![Donate](https://img.shields.io/badge/Donate-PayPal-green.svg)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=MQALEWTEZ7HX8)

<a href='https://ko-fi.com/S6S11K63U' target='_blank'><img height='36' style='border:0px;height:36px;' src='https://az743702.vo.msecnd.net/cdn/kofi1.png?v=2' border='0' alt='Buy Me a Coffee at ko-fi.com' /></a>

## About this repository

**IMPORTANT: the code in this repository is the base for dopameme 3. It is still work in progress and building it, does NOT provide you with a functional audio player. If you want a functional audio player, try <a href="https://www.digimezzo.com/content/software/dopameme/">dopameme 2</a> instead. The source code of dopameme 2 can be found <a href="https://github.com/digimezzo/dopameme-windows">here</a>.**

## Build prerequisites for GNU/Linux

-   rpm: required to build rpm package
-   libarchive-tools: contains bsdtar, which is required to build pacman package.

**To install the prerequisites on Ubuntu:**

`sudo apt install wine rpm libarchive-tools`

## Build prerequisites for Windows

Open a PowerShell prompt as Administrator and run this command to instal the Windows build tools:

`npm install --global --production windows-build-tools --vs2015`

## Build instructions

Due to the native dependency better-sqlite3, this project cannot be built for all platforms on GNU/Linux. The GNU/Linux packages must be built on GNU/Linux. The Windows package must be built on Windows. For mac, you're on your own. I have no means to test it out.

```bash
$ git clone https://github.com/digimezzo/dopameme.git
$ cd dopameme
$ npm install                # Install dependencies
$ npm run rebuild-sqlite     # Rebuild better-sqlite3 for the version of node.js which is used by Electron
$ npm start                  # Start dopameme
$ npm run electron:windows   # Build for Windows
$ npm run electron:linux     # Build for Linux
$ npm run electron:mac       # Build for Mac
```

## Pacman installation notes

The pacman package contains a dependency to package libappindicator-sharp, which is no longer distributed with Arch Linux. I cannot remove this dependency for now, because it is an issue in electron-builder (the packaging tool which is used in this project). It is, however, possible to install Knowte on Arch Linux or Manjaro using this command (replace x.y.z with the correct version number):

`$ sudo pacman -U Knowte-x.y.z.pacman --assume-installed libappindicator-sharp`
