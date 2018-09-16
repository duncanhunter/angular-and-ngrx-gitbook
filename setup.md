---
description: >-
  In this section we will configure our machines to get the most from this
  workshop.
---

# Setup

Dependency checklist:

1. node \(version 8 later\)
2. Git
3. Angular CLI
4. Visual Studio Code
5. Visual Studio Code Extensions

The main dependency for being able to make an Angular application is node version 8+. The latest stable version of node is best to get if you do not have it already installed.

## 1. Install node

You can check your version of node by running the following command in the terminal.

```text
node -v
```

If you do not have node installed or you are using a version lower than v4 then I you can get the latest stable version from [www.nodejs.org](https://github.com/duncanhunter/Enterprise-Angular-Applications-With-NgRx-and-Nx-Book/tree/d63a57a9f1ea36a7623cdf0746dd90b1406edaa2/www.nodejs.org).

## 2. Install Git

You can check your version of node by running the following command in the terminal.

```text
git --version
```

If you would like to use source control and check out completed work then it is recommended to have git installed on your machine. You can download git from[ https://git-scm.com/downloads ](https://git-scm.com/downloads%20)



## 3. Install Angular CLI 

We need to have the Angular CLI installed globally. Run the following command.

```text
npm install -g @angular/cli
```

## **4. Get Visual Studio Code**  

{% embed data="{\"url\":\"https://code.visualstudio.com/\",\"type\":\"link\",\"title\":\"Visual Studio Code - Code Editing. Redefined\",\"description\":\"Visual Studio Code is a code editor redefined and optimized for building and debugging modern web and cloud applications.  Visual Studio Code is free and available on your favorite platform - Linux, macOS, and Windows.\",\"icon\":{\"type\":\"icon\",\"url\":\"https://code.visualstudio.com/favicon.ico\",\"width\":128,\"height\":128,\"aspectRatio\":1},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"http://code.visualstudio.com/opengraphimg/opengraph-home.png\",\"width\":1223,\"height\":630,\"aspectRatio\":0.5151267375306623}}" %}

![](.gitbook/assets/image%20%2812%29.png)

## 5. Get **Visual Studio Code** Extensions

![The VSCode extension button](.gitbook/assets/image%20%285%29.png)

* Angular Essentials: Everything you need for angular in an extension pack
* Rainbow Brackets: Handy for many brackets when inlining observables
* TSLint: Great linting in VS Code
* Wallaby.js for unit tests line

{% embed data="{\"url\":\"https://marketplace.visualstudio.com/items?itemName=johnpapa.angular-essentials\",\"type\":\"link\",\"title\":\"Angular Essentials - Visual Studio Marketplace\",\"description\":\"Extension for Visual Studio Code - Essential extensions for Angular developers\",\"icon\":{\"type\":\"icon\",\"url\":\"https://marketplace.visualstudio.com/favicon.ico\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://johnpapa.gallerycdn.vsassets.io/extensions/johnpapa/angular-essentials/0.3.2/1508504847990/Microsoft.VisualStudio.Services.Icons.Default\",\"width\":128,\"height\":128,\"aspectRatio\":1},\"caption\":\"Angular essentials extension\"}" %}

{% embed data="{\"url\":\"https://marketplace.visualstudio.com/items?itemName=2gua.rainbow-brackets\",\"type\":\"link\",\"title\":\"Rainbow Brackets - Visual Studio Marketplace\",\"description\":\"Extension for Visual Studio Code - A rainbow brackets extension for VS Code.\",\"icon\":{\"type\":\"icon\",\"url\":\"https://marketplace.visualstudio.com/favicon.ico\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://2gua.gallerycdn.vsassets.io/extensions/2gua/rainbow-brackets/0.0.6/1474455607820/Microsoft.VisualStudio.Services.Icons.Default\",\"width\":128,\"height\":128,\"aspectRatio\":1},\"caption\":\"Rainbow brackets extension\"}" %}

{% embed data="{\"url\":\"https://marketplace.visualstudio.com/items?itemName=eg2.tslint\",\"type\":\"link\",\"title\":\"TSLint - Visual Studio Marketplace\",\"description\":\"Extension for Visual Studio Code - TSLint for Visual Studio Code\",\"icon\":{\"type\":\"icon\",\"url\":\"https://marketplace.visualstudio.com/favicon.ico\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://eg2.gallerycdn.vsassets.io/extensions/eg2/tslint/1.0.30/1527489705111/Microsoft.VisualStudio.Services.Icons.Default\",\"width\":120,\"height\":120,\"aspectRatio\":1},\"caption\":\"TSLint extention\"}" %}

![WallabyJS extension](.gitbook/assets/image%20%2814%29.png)

## 6. Optionally turn on **Visual Studio Code  auto save**

![VSCode auto save feature](.gitbook/assets/image%20%2817%29.png)

## 7. Update VS Code user settings to use single quotes and warnings for lint rules

* Open the command palette by pressing Ctrl + Shift + P and search for 'Preferences: Open User Settings'.
* Click the ellipsis and select 'Open settings.json' as shown in the following image.

![Open User Settings \(settings.json\)](.gitbook/assets/image%20%284%29.png)

* Add to your user settings the below options.
* Note that many people like to hide the Open Editors explorer on the top right as it is just a list of open tabs which you can see on the tabs themselves.

```javascript
{
    "tslint.alwaysShowRuleFailuresAsWarnings": true,
    "explorer.openEditors.visible": 0,
    "prettier.singleQuote": true
}
```

