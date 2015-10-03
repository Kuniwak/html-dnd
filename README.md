HTML Drag and Drop Simulator
============================

[HTML Drag and Drop](https://html.spec.whatwg.org/multipage/interaction.html#dnd) Simulator for E2E testing.

Now, [WebDriver](http://www.w3.org/TR/webdriver/) cannot handle HTML Drag and Drop.
This module can simulate the HTML Drag and Drop by using the [Execute Script command](http://www.w3.org/TR/webdriver/#execute-script).

This module is like [rcorreia/drag_and_drop_helper.js](https://gist.github.com/rcorreia/2362544), but it does not require jQuery.


Install
-------
```shell
npm install --save-dev html-dnd
```


Usage
-----
### For selenium-webdriver

```javascript
var dragAndDrop = require('html-dnd').code;
var webdriver = require('selenium-webdriver');
var By = webdriver.By;

var driver = new webdriver.Builder()
  .forBrowser('firefox')
  .build();

driver.get('http://example.com');

var draggable = driver.findElement(By.id('draggable'));
var droppable = driver.findElement(By.id('droppable'));

driver.execute(dragAndDrop, draggable, droppable);

driver.quit();
```


### For Nightwatch.js

```javascript
var dragAndDrop = require('html-dnd').codeForSelectors;

module.exports = {
  'drag and drop': function(browser) {
    browser
      .url('http://example.com')
      .execute(dragAndDrop, '#draggable', '#droppable')
      .end();
  }
};
```


### For WebdriverIO

```javascript
var dragAndDrop = require('html-dnd').codeForSelectors;
var webdriverio = require('webdriverio');
var options = { desiredCapabilities: { browserName: 'chrome' } };
var client = webdriverio.remote(options);

client
  .init()
  .url('http://example.com')
  .execute(dragAndDrop, '#draggable', '#droppable');
  .end();
```


See also
--------

- [Issue 3604: HTML5 Drag and Drop with Selenium Webdriver](https://code.google.com/p/selenium/issues/detail?id=3604)


License
-------

MIT
