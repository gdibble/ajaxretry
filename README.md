# ajaxRetry

#### Exponentially retry $.ajax requests

&nbsp;

## Installation

```
npm install --save ajaxretry
```

&nbsp;<br>In your client app `main.js`, add the following line to default retry settings:

```javascript
require('ajaxretry');
```

Or override any of the default settings using `set`: passing keyword arguments

```javascript
require('ajaxretry').set({ y:0.3 });
```

&nbsp;

## Usage
The default settings are:

```javascript
{
  base: 2.718281828,
  y: 0.25,
  retryCount: 3
}
```

&nbsp;

For `$.ajax` requets (also shorthand `$.get` and `.post`), pass `exhaust` in the options object as a callback function to run when retries fail
  * please note that `exhaust` supersedes the `error` callback
  * if `exhaust` method is not passed, retries will end without further action
  * the returned `jqXHR` object has been extended with the ajax request options, <br>thus allowing `jqXHR.type`, `jqXHR.url`, etcetera

```javascript
$.ajax({
  url: '/test',
  type: 'GET',
  exhaust : function (jqXHR, textStatus, errorThrown) {
    // Handle Internal Server Error
  }
});
```
&nbsp;

---

* **Changelog &gt;&gt;&gt;** [releases](https://github.com/gdibble/ajaxretry/releases)

---

* **Dependency:** [Underscore.js](http://underscorejs.org/)
  * ***Implied:***
    * [jQuery](http://jquery.com), [zepto.js](http://zeptojs.com), [ENDER](http://ender.jit.su) **or** even your own `$` library *which defines `$.ajax`*

---

* [npmjs.org/package/ajaxretry](https://www.npmjs.org/package/ajaxretry)

&nbsp;

&nbsp;

*This module is a simplified version of [backbone-ajaxretry](https://github.com/gdibble/backbone-ajaxretry) by the same author.*
