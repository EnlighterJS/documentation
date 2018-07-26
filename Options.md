EnlighterJS Options/Configuration
=====================================

EnlighterJS provides two mechanisms to pass options to the highlighting engine:

* Javascript options (global scope)
* HTML Data Attributes (local scope)

## Priorities ##

The 3 different types of options (defaults, js options, html attributes) are merged to from the **individual** element configuration

Priority Chain: `Default Options` **<** `Javascript Options` **<** `HTML Attributes` => `Current Configuration`

## Javascript Options (global) ##

The following options can be passed to Enlighter during the initialization via javascript as object

**Methods**

* `EnlighterJS.enlighte(el:DOMElement, options:Object)`
* `EnlighterJS.init(blockSelector:String, inlineSelector:String, options:Object)`

### ::language ###

* Description: sets the language support file which should be used to highlight the code
* Type: `string`
* Default: `generic`

**Example**

```js
// grab the element which should be highlighted
const myElement = document.getElementById('myCodeElement');

// highlight it, use javascript as language
EnlighterJS.enlight(myElement, {
    language: 'javascript'
})
```

### ::theme ###

* Description: sets the theme (css class) which should be used to display the highlighted code
* Type: `string`
* Default: `enlighter`

**Example**

```js
// highlight it, use javascript as language and bootstrap4 as theme
EnlighterJS.enlight(myElement, {
    language: 'javascript',
    theme: 'bootstrap4'
})
```

### ::indent ###

* Description: replaces tabs within the code with `n` spaces - recommended to avoid invalid indentations
* Type: `int`
* Default: `4`

**Example 1**

```js
// use only 2 spaces as indentation
EnlighterJS.enlight(myElement, {
    indent: 2
})
```

**Example 2**

```js
// don't replace tabs with spaces (not recommended)
EnlighterJS.enlight(myElement, {
    indent: false
})
```


### ::linehover ###

* Description: highlight code lines on-hover
* Type: `boolean`
* Default: `true`

**Example**

```js
// disable line-hover effect
EnlighterJS.enlight(myElement, {
    linehover: false,
    language: 'javascript',
    theme: 'bootstrap4'
})
```

### ::linenumbers ###

* Description: show linenumbers (`ol` container is used instead of `ul`)
* Type: `boolean`
* Default: `true`

**Example**

```js
// disable linenumbers
EnlighterJS.enlight(myElement, {
    linenumbers: false,
    language: 'javascript',
    theme: 'bootstrap4'
})
```

### ::lineoffset ###

* Description: sets the line-offset (initial line number) of the `ol` container
* Type: `int`
* Default: `0`

**Example**

```js
// start line enumeration with line 534
EnlighterJS.enlight(myElement, {
    lineoffset: 534,
    language: 'javascript',
    theme: 'bootstrap4'
})
```

### ::highlight ###

* Description: highlights a set of lines of the current codeblock. comma-separated sets and ranges are allowed
* Type: `string`
* Default: `<empty>`

**Example 1**

```js
// highlight line 1,2,3 + 5,9
EnlighterJS.enlight(myElement, {
    highlight: '1-3,5-9'
})
```

**Example 2**

```js
// highlight line 678-679
// relative to the lineoffset option - lines 9-10 are highlighted
EnlighterJS.enlight(myElement, {
    lineoffset: 670
    highlight: '678,679'
})
```

### ::rawcodeDbclick ###

* Description: toggle raw-code pane on doubleclick the current code
* Type: `boolean`
* Default: `false`

**Example**

```js
// toggle raw code on db-click
EnlighterJS.enlight(myElement, {
    rawcodeDbclick: true
})
```

### ::layout ###

* Description: selects the **JSX** based **View-Model** to render+display the highlighted code (adds outer wrapper and invokes the renderer)
* Type: `String`
* Default: `standard`

**Example 1**

```js
// use codegroup layout
EnlighterJS.enlight([myElement1, myElement2, myElement3], {
    layout: 'codegroup',
    theme: 'dracula'
})
```

**Example 2**

```js
// use inline layout
EnlighterJS.enlight(myInlineElement, {
    layout: 'inline',
    theme: 'dracula'
})
```

### ::ampersandCleanup ###

* Description: converts the escape sequence `&amp;` to `&` before highlighting the code (should be enabled)
* Type: `boolean`
* Default: `true`

**Example**

```js
// do not convert escaped ampersand
EnlighterJS.enlight(myElement, {
    ampersandCleanup: false
})
```











* **language** - (string) The default language used if no `data-enlighter-language` attibutes are used - default: **"generic"**
* **theme** - (string) The default theme used if no `data-enlighter-theme` attibutes are used - default: **"enlighter"**
* **indent** - (integer) Number of spaces to replace tabs with (-1 means no replacement) - default: **4**

## HTML Attribute Options (local) ##

