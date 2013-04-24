# StartHQ Extractor API

## Overview

[StartHQ](https://starthq.com) is a web app directory that provides info such as the speed of the app, its popularity, reliability, related news, recent blog posts etc. The directory is kept automatically up to date with API integrations, which are implemented via "extractors".

Extractors are CommonJS modules that typically use the synchronous Common Node [httpclient](http://olegp.github.io/common-node/doc/httpclient/index.html) interface for making HTTP requests.

This repo is a sample extractor that you can fork to implement your own. We will run your extractor on our infrastructure against the directory, include the data it provides on the app pages, and give it back to you via a RESTful API. You can use this data wherever you want, but please do link back to us.

Some ideas for extractors include:

- an extractor that checks whether the given web app is available as a native mobile in an app store such as Google Play Market
- an extractor that identifies which infrastructure provider the web app uses, e.g. Amazaon, Azure, App Engine etc.
- an extractor that uses the Twitter API to list all popular tweets about the app

For more ideas, check out the [StartHQ Roadmap](http://starthq.uservoice.com).

## Setup

First make sure you have Node.js installed from [http://nodejs.org](http://nodejs.org). NPM should be bundled with Node, so use that to install [Common Node](http://olegp.github.io/common-node/) with `npm install common-node -g` (you may need to prefix that `sudo` on Mac and Linux).

Fork this repo by clicking the "Fork" button in the upper right of this page, then clone your fork with `git clone git@github.com:USERNAME/extractor.git` (substituting your username for USERNAME) then change to the project directory with `cd extractor`.

To run, simply type `common-node .`

## API


<code>
var get = require("ringo/httpclient").get;

module.exports = function(app, config) {
	return get(app.url).content.length;
}
</code>

### Examples

Some example extractors are included in the `examples` subdirectory:

- wot - uses the Web of Trust API

### Sample App Data

### Dependencies

If your extractor has dependencies other than Common Node, please include an NPM compatible package.json file. To avoid proliferation of dependencies, we recommend using the following packages for some standard tasks:

- xml2s - for parsing XML

### Support

If you run into any problems or want to let us know about your extractor so we can merge it in, either create an issue under this repo, or e-mail us at developers@starthq.com

### License

__Note that you need to retain this license with an updated copyright line in your fork in order for us to be able to run your extractor.__

(The MIT License)

Copyright (c) 2013+ StartHQ

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
'Software'), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
