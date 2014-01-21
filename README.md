# css-url-rewriter [![Build Status](https://secure.travis-ci.org/callumlocke/css-url-rewriter.png?branch=master)](http://travis-ci.org/callumlocke/css-url-rewriter)

A simple function that looks for `url(...)` definitions in CSS and runs them through your rewriter function.


## Getting Started
Install the module with: `npm install css-url-rewriter`

```javascript
var rewriteCSSURLs = require('css-url-rewriter');

// Example - add a query string to all URLs
var newCSS = rewriteCSSURLs(someCSS, function (url) {
  return url + '?12345'
});
```

It will process all URLs it encounters by default, even `data:` URIs, so you need to check for those manually if you want to handle them differently.


### Settings
You can optionally pass in a settings object, like this:

```javascript
var newCSS = rewriteCSSURLs(someCSS, settings, function (url) {
  return url + '?12345'
});
```

Currently there is only one configurable setting, `excludedProperties`, which is an array of properties that you want to skip. This setting defaults to `['behavior', '*behavior']` (because you usually don't want to mess with URLs in this proprietary MSIE property, since they have weird rules associated with them).


## License
Copyright (c) 2014 Callum Locke. Licensed under the MIT license.
