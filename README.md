#Twitter Bootstrap 2.0.1 with HTML5 Boilerplate 3.0 styles ported to Stylus

All the credit goes to the [Twitter Bootstrap](https://github.com/twitter/bootstrap) and [HTML5 Boilerplate](https://github.com/h5bp/html5-boilerplate) guys and gals as well as @visionmedia for [nib](https://github.com/visionmedia/nib).

## What is it?

If you haven't already, go read about [Twitter Bootstrap](http://twitter.github.com/bootstrap/) and [HTML5 Boilerplate](http://html5boilerplate.com/).

This project only uses the css portion of HTML5 Boilerplate.  Since both Twitter Bootstrap 2.0 and HTML5 Boilerplate include/are based on [normalize.css](https://github.com/necolas/normalize.css/), there is a lot of overlap, but Bootstrap does not include everything.  I have included here only the parts of HTML5 Boilerplate that I saw were missing in Bootstrap.

This project also now includes a customized version of [nib](https://github.com/visionmedia/nib) so all the goodness of nib is automatically available for your custom styles.  The reason it is a customized version is to bring its output more in line with Twitter Bootstrap's output.  Everything still works the same, only some of the `vendor` mixins now only output for the vendors that have actually implemented those prefixed styles.

## Changes in final CSS from the official Twitter Bootstrap 2.0.1

Below used to be a list of everything you should see if you do a diff on the outputted bootstrap.css and the official version.  Since updating to use `nib`, this is not entirely accurate, but it will give you an idea of the differences.  Most of the changes in the css make no semantic difference, although some do.

* Stylus stacks multiple selectors instead of placing them on one line:
	* Instead of `audio, canvas, video` on one line, you get them on three lines.
* Stylus minimizes the length of colors, so it outputs #333 instead of #333333.
* Stylus only has 2 decimal precision so where the official css has 0.075, Stylus outputs 0.07 and for 0.025, stylus outputs 0.03 (why it rounds up in one place and not in another is a mystery to me).  It also adds an extraneous 0 when only one decimal place is need (0.2 is output as 0.20).
* Stylus adds quotations marks around `url`, so `background-image: url(../img/glyphicons-halflings.png)` becomes `background-image: url("../img/glyphicons-halflings.png")`
* Stylus removes spaces between values in `rgba`, so `rgba(0, 0, 0, 0.2)` becomes `rgba(0,0,0,0.20)`.
* Stylus automatically adds vendor prefixes, which corrected an error in the official Less version where in `.dropdown-menu`, `-moz-background-clip` was set to `padding` instead of `padding-box`.
* Stylus enables calling mixins transparently (e.g. `opacity: 1` is the same as `opacity(1)` if there is a mixin named `opacity`).  In the official Less files, there is a mixin named `opacity` but they did not use it everywhere they set opacity.  So in the output from Stylus, you will see an additional `filter: alpha(opacity=0)` or similar in some places.
* On `.alert`, the border color is slightly different due to a difference in the `spin` function in Stylus vs. the one on Less.  so it outputs as `#fbefd5` instead of `#fbeed5`.  I decided the difference was not great enough to warrent trying to rewrite the `spin` function.
* Apparently, my `darken` function for Less compatability is not perfect, because `.btn-navbar:active...` has `background-color: #090909` instead of `#080808`.
* @keyframes is handled differently in Stylus.  It changes `from` to `0%` and `to` to `100%` which they claim is the official syntax (I haven't checked).  It also adds vendor prefixes for Opera and IE.  I assume due to a bug, these are all output at the end of rendering `progress-bars.styl`.  This should not change the semantics at all.
* I added `-ms-filter: progid:DXImageTransform.Microsoft.Alpha(Opacity=$opacity)` to the `opacity` mixin to support IE8 (http://www.quirksmode.org/css/opacity.html).

And that's it!  I have included the rendered css files so you can run your own diff and check, if you like before you try using this.

The official minimized bootstrap.min.css is 71.5kb while the minimized version from Stylus is 69.8kb.  This is due to leaving off the final semicolon in style definitions (although sometimes it is there?), removing the spaces in `rgba` and using the short form of hex colors.

## How to use

First, you need to get [Stylus](http://learnboost.github.com/stylus/).  This requires [node.js](http://nodejs.org/) to be installed on your system.

```bash
$ npm install stylus
```

Next, download the project.

```bash
$ git clone https://github.com/flowonyx/bootstrap-h5bp-stylus.git
```

```bash
$ cd bootstrap-h5bp-stylus
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

Copyright and license for any changes made
------------------------------------------
Anything added/changed, etc. which does not fall under the licensing of HTML5 Boilerplate or Twitter Bootstrap 2.0.1 is released to the Public Domain.

Copyright and license for HTML5 Boilerplate
-------------------------------------------
The parts included here are released to the Public Domain.

Copyright and license for Twitter Bootstrap 2.0.1
-------------------------------------------------

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

Glyphicons use in Twitter Bootstrap 2.0.1
-----------------------------------------

From the Twitter Bootstrap 2.0.1 docs:

[Glyphicons](http://glyphicons.com/) has granted us use of the Halflings set in our open-source toolkit so long as we provide a link and credit here in the docs. Please consider doing the same in your projects.
