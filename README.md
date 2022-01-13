# nut.js (Native UI Toolkit) 

|	|GitHub Actions|
|:-:	|:-:	|
|Master |![Create tagged release](https://github.com/nut-tree/nut.js/workflows/Create%20tagged%20release/badge.svg)|
|Develop|![Create snapshot release](https://github.com/nut-tree/nut.js/workflows/Create%20snapshot%20release/badge.svg)|

[![SonarCloud badge](https://sonarcloud.io/api/project_badges/measure?project=nut-tree%3Anut.js&metric=alert_status)](https://sonarcloud.io/dashboard?id=nut-tree%3Anut.js)
[![SonarCloud Coverage](https://sonarcloud.io/api/project_badges/measure?project=nut-tree%3Anut.js&metric=coverage)](https://sonarcloud.io/component_measures?id=nut-tree%3Anut.js&metric=coverage)

[![Downloads per month](https://img.shields.io/npm/dm/@nut-tree/nut-js)](https://www.npmjs.com/package/@nut-tree/nut-js)

<p align="center">
Please visit
</p>
<h1 align="center"><a href="https://nutjs.dev">nutjs.dev</a></h1>
<p align="center">
for detailed documentation and tutorials
</p>

<br/>

# About

<p align="center">
    <img src="https://github.com/nut-tree/nut.js/raw/master/.gfx/nut.png" alt="logo" width="200"/>
</p>

`nut.js` is a cross-platform native UI automation / testing tool.

It allows for native UI interactions via keyboard and / or mouse,
but additionally gives you the possibility to navigate the screen based on image matching.

# Sponsoring

`nut.js` is developed with community in mind.

A huge **"Thank you!"** goes out to all sponsors who make open source a bit more sustainable!

[<img src="https://avatars.githubusercontent.com/u/17616211?v=4" width="75" alt="Reiss Cashmore" />](https://github.com/Reiss-Cashmore)
[<img src="https://avatars.githubusercontent.com/u/1794527?v=4" width="75" alt="Chet Corcos" />](https://github.com/ccorcos)
[<img src="https://avatars.githubusercontent.com/u/562800?v=4" width="75" alt="Stephan Petzl" />](https://github.com/stoefln)

<hr/>

[<img src="https://github.com/nut-tree/nut.js/raw/develop/.gfx/sponsors/mighty.svg" height="75" alt="Mighty browser logo"/>](Mighty Browser)


# Demo

Check out this demo video to get a first impression of what nut.js is capable of.

[![nut.js demo video](https://img.youtube.com/vi/MpIyUJnU_Bk/1.jpg)](https://www.youtube.com/watch?v=MpIyUJnU_Bk)

# Tutorials

Please consult the project website at [nutjs.dev](https://nutjs.dev/docs/tutorial-first_steps/prerequisits) for in-depth tutorials

# Examples

[nut-tree/trailmix](https://github.com/nut-tree/trailmix) contains a set of ready to use examples which demo the usage ot nut.js.

# API Docs

nut.js provides [public API documentation](https://nut-tree.github.io/apidoc/) auto-generated by [TypeDoc](https://typedoc.org).

# Community

Feel free to join our [Discord community](https://discord.gg/sJkN7789XR)

# Modules

This list gives an overview on currently implemented and planned functionality.
It's work in progress and will undergo constant modification.

## Clipboard

- [x] Copy text to clipboard
- [x] Paste text from clipboard

## Keyboard

- [x] Support for standard US keyboard layout
- [x] Support for multimedia keys

## Mouse

- [x] Support for mouse movement
- [x] Support for mouse scroll
- [x] Configurable movement speed
- [x] Mouse drag

## Window

- [x] List all windows
- [x] Retrieve active window
- [x] Retrieve window title
- [x] Retrieve window size and position

## Screen

- [x] Find an image on screen (requires an additional provider package like e.g. [nut-tree/template-matcher](https://www.npmjs.com/package/@nut-tree/template-matcher))
- [x] Find all image occurrences on screen
- [x] Wait for an image to appear on screen (requires an additional provider package like e.g. [nut-tree/template-matcher](https://www.npmjs.com/package/@nut-tree/template-matcher))
- [x] Retrieve RGBA color information on screen
- [x] Hooks to trigger actions based on images (requires an additional provider package like e.g. [nut-tree/template-matcher](https://www.npmjs.com/package/@nut-tree/template-matcher))
- [x] Highlighting screen regions

## Integration

- [x] Jest
- [x] Electron

# Sample

The following snippet shows a valid `nut.js` example:

```js
"use strict";

const { mouse, left, right, up, down, straightTo, centerOf, Region} = require("@nut-tree/nut-js");

const square = async () => {
  await mouse.move(right(500));
  await mouse.move(down(500));
  await mouse.move(left(500));
  await mouse.move(up(500));
};

(async () => {
    await square();
    await mouse.move(
        straightTo(
            centerOf(
                new Region(100, 100, 200, 300)
            )
        )
    );
})();
```

# Installation

## Prerequisites

This section lists runtime requirements for `nut.js` on the respective target platform.

#### Windows

In order to install `nut.js` on Windows, please make sure to have the [Microsoft Visual C++ Redistributable](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) installed.

In case you're running Windows 10 N, please make sure to have the [Media Feature Pack](https://support.microsoft.com/en-us/topic/media-feature-pack-for-windows-10-n-may-2020-ebbdf559-b84c-0fc2-bd51-e23c9f6a4439) installed as well.

#### macOS

On macOS, Xcode command line tools are required.
You can install them by running
```bash
xcode-select --install
```

**Attention**:

In case you're experiencing problems like your mouse not moving or your keyboard not typing,
please make sure to give the process you're executing your tests with accessibility permissions.

nut.js will give you a subtle hint in case permissions are lacking:

`##### WARNING! The application running this script is not a trusted process! Please visit https://github.com/nut-tree/nut.js#macos #####`

When an application wants to use accessibility features, a permission pop-up should be shown.
If not, you could try to manually add the application you're running the script from.

`Settings -> Security & Privacy -> Privacy tab -> Accessibility -> Add...`

For example, if you want to execute your node script in e.g. `iTerm2`, you'd have to add `iTerm.app` to the list.
When running your script from a built-in terminal in e.g. `VSCode` or `IntelliJ`, you'd have to add the respective IDE.

<p align="center">
    <img src="https://github.com/nut-tree/nut.js/raw/develop/.gfx/permissions.png" alt="accessibility permissions screen"/>
</p>

#### Linux

Depending on your distribution, Linux setups may differ.

In general, `nut.js` requires

- libXtst

Installation on `*buntu` distributions:
```bash
sudo apt-get install libxtst-dev
```

Setups on other distributions might differ.

## Install `nut.js`

Running 

```bash
npm i @nut-tree/nut-js
```

or

```bash
yarn add @nut-tree/nut-js
```

will install `nut.js` and its required dependencies.

### Snapshot releases

`nut.js` also provides snapshot releases which allows to test upcoming features.

Running 

```bash
npm i @nut-tree/nut-js@next
```

or

```bash
yarn add @nut-tree/nut-js@next
```

will install the most recent development release of `nut.js`.

**Attention**: While snapshot releases are great to work with upcoming features before a new stable release, it is still a snapshot release.
Please bear in mind that things might change and / or break on snapshot releases, so it is not recommended using them in production.
