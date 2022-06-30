# ChromiteX-preview
Chromium meets Eclipse VertX and both together want to go on a journy follow them and be a part of it


## Usage

### Linux Only At present
go to releases on github

Download the current Preview Release it is a Bundled GraalVM Community Edition Modifyed with some stuff
I did not create a installer for it at present so for this Preview it is the most best to ship the whole Stack

You can use the internal Package Manager chromi-pm it is like npm and can be used as 1:1 replacement for it in
this stack it has some default assumptions and will install anything directly inside the stacks folder this
is by design as later in the final version we will allow you to transition to systemwide install and also
run build and deploy Your Apps Packaged or as a platform.

### Example ECMAScript Code Inside ES4X or graal-node
Simple Example that shows how to Communicate via elementHandels

```js
const chromitex = require('chromitex');

let uff = 1;

// HTML Template String
const loadingPage2 = `<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>APP</title>
  <style>
  html, body {
    margin: 0; padding: 0;
    height: 100%; width: 100%;
    background: #333; color: white;
  }
  </style>
</head>
<body>
    <a href="https://domain">GO</a><p>${uff = uff * 2}</p>    
</body>
</html>`

const appMode = {
  headless: false,
  ignoreDefaultArgs: [
    '--enable-automation',
    '--remote-debugging-port=0',
    '--enable-blink-features=IdleDetection'
  ],
  args: [
    `--app=data:text/html,${loadingPage}`,
    '--no-default-browser-check',
  ]
  //userDataDir: './myUserDataDir',
};

class: ElementHandle
extends: JSHandle
ElementHandle represents an in-page DOM element. ElementHandles can be created with the page.$ method.

const puppeteer = require('puppeteer');

(async () => {
  const browser = await puppeteer.launch();
  const page = await browser.newPage();
  await page.goto('https://example.com');
  const hrefElement = await page.$('a');
  await hrefElement.click();
  // ...
})();



```

background we introduce the following abstractions as References to the original dom Elements in the Chromium Context elementHandel.

this is a short list of methods for it:

```
ElementHandle prevents DOM element from garbage collection unless the handle is disposed. ElementHandles are auto-disposed when their origin frame gets navigated.

ElementHandle instances can be used as arguments in page.$eval() and page.evaluate() methods.

Methods
elementHandle.$(selector)
elementHandle.$$(selector)
elementHandle.$$eval(selector, pageFunction[, ...args])
elementHandle.$eval(selector, pageFunction[, ...args])
```


## Faq

1. This ships with chromium can i directly use my Installed Browser?
***answer*** Yes you could probally already do that but this is out of scope for this preview but sure this is a part of ChromiteX
2. sharedArray Buffers directly inside all Contexts? 
***answer*** No Not at present but it is a higher goal will be enabled once v8 got fully replaced at present we interOp with it between graal-node => IPC => Chromium (v8)
3. Can i Run Some Scala Code inside the browser? 
***answer*** Yes you can write some scala code and let it build and run you can also exchange data via callbacks over the ipc 

- [ ] es4x-chromium
- [ ] vertx-chromium
- [ ] vertx-devtools
