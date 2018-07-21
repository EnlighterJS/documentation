Developer Guide
===============

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

Highlighting-Engine and Symbols
-------------------------------

The Highlighting-Engine is based on syntactic **tokens**. Tokens are organized in logical groups, e.g. comments, numbers, keywords.
Each token belongs to a type which is composed of its group and group-number, related to the scheme **group[a-z]{1}number[0-9]{1,2}**. 
E.g. `c4` (group comments, number 5). This type is used to define styles for each syntax-element.

To provide a language-coherent appearance, each token type has only to be used for its specific purpose!

### Comments ###

Prefix: **c**

* **c0** | Single Line Comments/General
* **c1** | Multi Line Block Comments
* **c2** | Multi Line Doc Comments
* **c9** | Special Comment Syntax

### Keywords ###

Prefix: **k**

* **k0** | Global Keywords
* **k1** | Control Structure Keywords
* **k2** | Variable/Type Initialization Keyword
* **k3** | Operators
* **k4** | Directives
* **k5** | Types
* **k6** | Labels/Symbols
* **k7** | Variable
* **k8** | Type Qualifiers/Modifier
* **k9** | Special Keywords
* **k10** | Namespaces

### Expressions/Literals ###

Prefix: **e**

* **e0** | Boolean Expressions
* **e1** | Null Expressions
* **e2** | Regular Expressions
* **e3** | Constants
* **e4** | Shell/Command Expression

### Strings ###

Prefix: **s**

* **s0** | General Strings
* **s1** | Characters
* **s2** | Template Strings
* **s3** | Template String Delimiter
* **s4** | String Escape Sequences
* **s5** | Multi Line Strings

### Numbers ###

Prefix: **n**

* **n0** | Floats/General Numbers
* **n1** | Integers
* **n2** | Hexadecimal
* **n3** | Binary
* **n4** | Octal
* **n5** | Complex/Imaginary Numbers

### Methods/Functions ###

Prefix: **m**

* **m0** | General/Global Function Calls
* **m1** | General/Dynamic Method Calls
* **m2** | Static Method Calls
* **m3** | Properties

### Generic ###

Prefix: **g**

* **g0** | Generic Symbols 
* **g1** | Brackets

### Language Specific ###

Prefix: **x**

* **x1** | XML Tag
* **x2** | XML Attribute
* **x10** | CSS ID Selector
* **x11** | CSS Class Selector
* **x12** | CSS Rule/Property
* **x13** | CSS Units
* **x14** | CSS Hex Colors
* **x15** | CSS Pseudo Elements/Selectors

### Text Documents ###

Prefix: **t**

* **t0** | Metadata
* **t1** | Heading
* **t2** | Section
* **t3** | Hyperlink
* **t4** | Emphasis/Formatting
* **t5** | OK/Positive (e.g. diff+)
* **t6** | Failure/Negative (e.g. diff-)
* **t7** | Quotes/Blockquotes
* **t8** | Code (not highlighted)

Language Development
--------------------

**Notice:** Language support files added to the `src/lang/` directory are **not automatically recognized** by the build system. You have to **edit** the `src/lang/index.js` file and add an export statement!

### Naming Scheme ###

Language names are always **lowercase**, consists of **letters and numbers** and **start with a letter**


Theme Development
-----------------

**Notice:** Your new theme is **not automatically recognized** by the build system. You have to **edit** the `gulpfile.js` and add your theme to the `themelist` array.

### Naming Scheme ###

Theme names are always **lowercase**, consists of **letters and numbers** and **start with a letter**
