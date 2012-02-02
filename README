#Twitter Bootstrap with HTML5 Boilerplate styles ported to Stylus

Sorry I couldn't think up a cool name.  It is what it is. :)

All the credit goes to the [Twitter Bootstrap](https://github.com/twitter/bootstrap) and [HTML5 Boilerplate](https://github.com/h5bp/html5-boilerplate) guys and gals.

## What is it?

If you haven't already, go read about [Twitter Bootstrap](http://twitter.github.com/bootstrap/) and [HTML5 Boilerplate](http://html5boilerplate.com/).

This project only uses the css portion of HTML5 Boilerplate.  Since both Twitter Bootstrap and HTML5 Boilerplate include/are based on [normalize.css](https://github.com/necolas/normalize.css/), there is a lot of overlap, but Bootstrap does not include everything.  I have included here only the parts of HTML5 Boilerplate that I saw were missing in Bootstrap.

## How to use

First, you need to get [Stylus](http://learnboost.github.com/stylus/).  This requires [node.js](http://nodejs.org/) to be installed on your system.

```bash
$ npm install stylus
```

#### Note that for any of these commands, you can pass stylus the -c option to get a minimized css file.

### Compiling everything into one css file
```bash
$ stylus style.styl
```
This will produce style.css which includes Twitter Bootstrap, including the responsive part, the missing HTML5 Boilerplate styles, and any custom styles you put in custom.styl and custom-responsive.styl.

### Compiling only Twitter Bootstrap without the responsive part
```bash
$ stylus bootstrap.styl
```
This will produce bootstrap.css which is equivalent to Twitter Bootstrap's bootstrap.css  + any custom styles you put in custom.styl and custom-responsive.styl.

### Compiling only the responsive part of Twitter Bootstrap
```bash
$ stylus bootstrap-responsive.styl
```
This will produce bootstrap-responsive.css which is equivalent to Twitter Bootstrap's bootstrap-responsive.css.

### Compiling only Twitter Bootstrap, including the responsive part
```bash
$ stylus responsive.styl
```
This will produce responsive.styl which is equivalent to Twitter Bootstrap's bootstrap.css + bootstrap-responsive.css + any custom styles you put in custom.styl and custom-responsive.styl.

## Other thoughts

To get Stylus to produce the same output as Less (in other words, to get the same colors from color manipulation functions), I had to write some custom mixins for Stylus that followed the same algorithms as Less.  These are in the less-compat.styl file.

All the HTML5 Boilerplate code is broken into their respective parts (each file begins with *h5bp-*) to make it easy if you want to remove part of it that you know you don't need.  Just comment out that *@import* in style.styl.

I certainly hope this is helpful to somebody.  It was an interesting exercise and now I'm looking forward to using it in my own projects.

Copyright and license for HTML5 Boilerplate
-------------------------------------------
The parts included here are released to the Public Domain.

Copyright and license for Twitter Bootstrap
-------------------------------------------

Copyright 2012 Twitter, Inc.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this work except in compliance with the License.
You may obtain a copy of the License in the LICENSE file, or at:

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.