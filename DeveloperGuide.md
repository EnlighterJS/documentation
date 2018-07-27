Developer Guide
===============

Index
----------------

* [Highlighting-Engine and Symbol](HighlightingEngine_and_Symbols.md)
* [Theme Development](#theme-development)
* [Language Development](#language-development)

Setup EnlighterJS Development Environment
------------------------------------------

**These instructions are targeted to Linux or MacOS users only - it should also work with Windows but it has not been tested yet!**

### Install required software packages ###

To setup a development environment (which contains the sourcecode and the build system) you have to install the following software packages on your machine:

1. [node.js](https://nodejs.org/en/download/) `>=8`
2. [yarn](https://yarnpkg.com/lang/en/)
3. [git](https://git-scm.com/downloads)

### Download sourcecode + packages ###

Clone the EnlighterJS sourcecode (git respository) and install npm packages.

```bash
# clone the GitHub repository into the current directory
git clone https://github.com/EnlighterJS/EnlighterJS.git .

# checkout master branch
git checkout master

# install the npm packages (required to build EnlighterJS)
# BTW: NEVER commit changes related to the yarn.lock or package.json file - these request will be rejected
yarn install
```

### Start watch mode (development) ###

EnlighterJS build environment comes with an embedded webserver (expressjs basesd) to serve the `Development.html` file.
It is recommended to use this file to develope new themes, language support files or fixing bugs - just edit it.

By starting the `gulp watch` mode, each modification of a file within the `src/` directory will re-trigger the build process. 
After you have made some changes on the javascript code, just reload your browser window and view the results!

**Example**

```bash
./gulp watch
[09:10:17] Using gulpfile ~/Development/EnlighterJS/core/gulpfile.js
[09:10:17] Starting 'transpiler'...
[09:10:17] Starting 'less-themes-full'...
[09:10:17] Starting 'webserver'...
[09:10:17] Finished 'webserver' after 4.19 ms
[09:10:17] DEV Webserver Online - localhost:8888
[09:10:19] Finished 'transpiler' after 1.57 s
[09:10:19] Starting 'bundle'...
[09:10:19] Finished 'bundle' after 501 ms
[09:10:19] Finished 'less-themes-full' after 2.16 s
[09:10:19] Starting 'watch'...
[09:10:19] Finished 'watch' after 78 ms
```

The `Development.html` becomes available on [http://localhost:8888](http://localhost:8888) - you can change the port within `gulpfile.js`

### Build the release files ###

Finally, run `gulp default` to trigger the default build process (EnlighterJS Engine + Single Themes + Full Themes).
All files are available within the `dist/` directory

```bash
$ ./gulp default
[09:28:10] Using gulpfile ~/Development/EnlighterJS/core/gulpfile.js
[09:28:11] Starting 'transpiler'...
[09:28:11] Starting 'less-themes-full'...
[09:28:11] Starting 'less-themes-single'...
[09:28:11] Finished 'less-themes-single' after 8.41 ms
[09:28:12] Finished 'transpiler' after 1.21 s
[09:28:12] Starting 'bundle'...
[09:28:12] Finished 'bundle' after 688 ms
[09:28:12] Finished 'less-themes-full' after 1.93 s
[09:28:12] Starting 'default'...
[09:28:12] Finished 'default' after 34 μs
```

### Contribution + Committing Changes ###

EnlighterJS is OpenSource and managed on [GitHub](https://github.com/EnlighterJS/EnlighterJS) - if you like, you're welcome to contribute!
To simplify the release and quality control process, please follow these remarks:

1. **One Enhancement** _==>_ **One Commit** (don't merge a bunch of changes in a single commit!)
2. Only commit changes to the `src/` or `examples/` directory. Otherwise your request will be rejected
3. Discuss larger project changes with the Maintainer **before implementing**
4. Use GitHub for question, bugreports and discussions

Language Development
--------------------

**Notice:** Language support files added to the `src/lang/` directory are **not automatically recognized** by the build system. You have to **edit** the `src/lang/index.js` file and add an export statement!

### Naming Scheme ###

Language names are always **lowercase**, consists of **letters and numbers** and **start with a letter**

### Examples ####

* **cpp** :heavy_check_mark:
* **rust** :heavy_check_mark:
* **c++** :x:
* **c-sharp** :x:
* **c#** :x:
* **visual-basic** :x:
* **visualbasic** :heavy_check_mark:

Theme Development
-----------------

**Notice:** Your new theme is **not automatically recognized** by the build system. You have to **edit** the `gulpfile.js` and add your theme to the `themelist` array.

### Naming Scheme ###

Theme names are always **lowercase**, consists of **letters and numbers** and **start with a letter**

### Examples ####

* **mytheme** :heavy_check_mark:
* **xtheme01** :heavy_check_mark:
* **lalala-theme** :x:
* **MY_ULTRA_THEME** :x:
* **00_MY_ULTRA_THEME** :x:
* **123456** :x:
