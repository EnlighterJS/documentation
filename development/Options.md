EnlighterJS Options/Configuration
=====================================

EnlighterJS provides two mechanisms to pass options to the highlighting engine.

Please keep in mind that these mechanisms are **not coherent** - each of them contains some special options which are only valid in the attribute scope or as javascript option!

### Javascript options (global scope) ###

* [language](#language)
* [theme](#theme)
* [indent](#indent)
* [linehover](#linehover)
* [linenumbers](#linenumbers)
* [lineoffset](#lineoffset)
* [highlight](#highlight)
* [textOverflow](#textOverflow)
* [rawcodeDbclick](#rawcodeDbclick)
* [layout](#layout)
* [ampersandCleanup](#ampersandCleanup)

### HTML Data Attributes (local scope) ###

* [data-enlighter-language](#data-enlighter-language)
* [data-enlighter-theme](#data-enlighter-theme)
* [data-enlighter-layout](#data-enlighter-layout)
* [data-enlighter-highlight](#data-enlighter-highlight)
* [data-enlighter-linenumbers](#data-enlighter-linenumbers)
* [data-enlighter-lineoffset](#data-enlighter-lineoffset)
* [data-enlighter-title](#data-enlighter-title)
* [data-enlighter-group](#data-enlighter-group)

## Priorities ##

The 3 different types of options (defaults, js options, html attributes) are merged to from the **individual** element configuration

Priority Chain: `Default Options` **<** `Javascript Options` **<** `HTML Attributes` => `Current Configuration`

## Javascript Options (global) ##

The following options can be passed to Enlighter during the initialization via javascript as object

**Methods**

* `EnlighterJS.enlighte(el:DOMElement, options:Object)`
* `EnlighterJS.init(blockSelector:String, inlineSelector:String, options:Object)`

-----------------------------------

### ::language ###

* Description: sets the language support file which should be used to highlight the code
* Type: `string`
* Default: `generic`
* Operation: internal

**Example**

```js
// grab the element which should be highlighted
const myElement = document.getElementById('myCodeElement');

// highlight it, use javascript as language
EnlighterJS.enlight(myElement, {
    language: 'javascript'
})
```

-----------------------------------

### ::theme ###

* Description: sets the theme (css class) which should be used to display the highlighted code
* Type: `string`
* Default: `enlighter`
* Operation: css flag

**Example**

```js
// highlight it, use javascript as language and bootstrap4 as theme
EnlighterJS.enlight(myElement, {
    language: 'javascript',
    theme: 'bootstrap4'
})
```

-----------------------------------

### ::indent ###

* Description: replaces tabs within the code with `n` spaces - recommended to avoid invalid indentations
* Type: `int`
* Default: `4`
* Operation: internal

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

-----------------------------------

### ::linehover ###

* Description: highlight code lines on-hover
* Type: `boolean`
* Default: `true`
* Operation: css flag

**Example**

```js
// disable line-hover effect
EnlighterJS.enlight(myElement, {
    linehover: false,
    language: 'javascript',
    theme: 'bootstrap4'
})
```

-----------------------------------

### ::linenumbers ###

* Description: show linenumbers (`ol` container is used instead of `ul`)
* Type: `boolean`
* Default: `true`
* Operation: css flag

**Example**

```js
// disable linenumbers
EnlighterJS.enlight(myElement, {
    linenumbers: false,
    language: 'javascript',
    theme: 'bootstrap4'
})
```

-----------------------------------

### ::lineoffset ###

* Description: sets the line-offset (initial line number) of the `ol` container
* Type: `int`
* Default: `0`
* Operation: css style

**Example**

```js
// start line enumeration with line 534
EnlighterJS.enlight(myElement, {
    lineoffset: 534,
    language: 'javascript',
    theme: 'bootstrap4'
})
```

-----------------------------------

### ::highlight ###

* Description: highlights a set of lines of the current codeblock. comma-separated sets and ranges are allowed
* Type: `string`
* Default: `<empty>`
* Operation: internal

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

-----------------------------------

### ::textOverflow ###

* Description: sets the text overflow mode (break line or horizontal scroll)
* Type: `string`
* Default: `break`
* Scope: `view:standard,codegroup`
* Operation: css flag
* Values: [`scroll`, `break`]

**Example 1**

```js
// enable horizontal scroll
EnlighterJS.enlight(myElement, {
    textOverflow: 'scroll'
})
```

-----------------------------------


### ::rawcodeDbclick ###

* Description: toggle raw-code pane on doubleclick the current code
* Type: `boolean`
* Default: `false`
* Operation: internal

**Example**

```js
// toggle raw code on db-click
EnlighterJS.enlight(myElement, {
    rawcodeDbclick: true
})
```

-----------------------------------


### ::layout ###

* Description: selects the **JSX** based **View-Model** to render+display the highlighted code (adds outer wrapper and invokes the renderer)
* Type: `String`
* Default: `standard`
* Operation: internal

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

-----------------------------------

### ::ampersandCleanup ###

* Description: converts the escape sequence `&amp;` to `&` before highlighting the code (should be enabled)
* Type: `boolean`
* Default: `true`
* Operation: internal

**Example**

```js
// do not convert escaped ampersand
EnlighterJS.enlight(myElement, {
    ampersandCleanup: false
})
```

-----------------------------------

## HTML Attribute Options (local) ##

EnlighterJS uses HTML5 data attribute to recognize element related options. These options have the **highest** priority and will override the javascript based ones!

-----------------------------------

### ::data-enlighter-language ###
* Description: sets the language support file which should be used to highlight the code
* Type: `string`
* Default: `generic`
* Scope: `ALL`

**Example**

```html
<!-- highlight rust code !-->
<pre data-enlighter-language="rust">
....
</pre>
```

-----------------------------------

### ::data-enlighter-theme ###

* Description: sets the theme (css class) which should be used to display the highlighted code
* Type: `string`
* Default: `enlighter`
* Scope: `ALL`

**Example**

```html
<!-- set theme to "atomic" - may usefull to use different codeblock styles within your page !-->
<pre data-enlighter-theme="atomic">
....
</pre>
```

-----------------------------------

### ::data-enlighter-layout ###

* Description: selects the **JSX** based **View-Model** to render+display the highlighted code (adds outer wrapper and invokes the renderer)
* Type: `String`
* Default: `standard`
* Scope: `ALL`

```html
<!-- use a custom layout to highlight the code !-->
<pre data-enlighter-layout="myCustomlayout">
....
</pre>
```

-----------------------------------

### ::data-enlighter-highlight ###

* Description: highlights a set of lines of the current codeblock. comma-separated sets and ranges are allowed
* Type: `string`
* Default: `<empty>`
* Scope: `view:standard,codegroup`

```html
<!-- highlight the line 4,10,11,12 !-->
<pre data-enlighter-highlight="4,10-12">
....
</pre>
```

-----------------------------------

### ::data-enlighter-linenumbers ###

* Description: show linenumbers (`ol` container is used instead of `ul`)
* Type: `boolean`
* Default: `true`
* Scope: `view:standard,codegroup`

```html
<!-- disable line numbers !-->
<pre data-enlighter-linenumbers="false">
....
</pre>
```

-----------------------------------

### ::data-enlighter-lineoffset ###

* Description: sets the line-offset (initial line number) of the `ol` container
* Type: `int`
* Default: `0`
* Scope: `view:standard,codegroup`

```html
<!-- set start of line-counter to 343 !-->
<pre data-enlighter-lineoffset="343">
....
</pre>
```

-----------------------------------

### ::data-enlighter-title ###

* Description: sets the tabpane title of a codegroup (view: `codegroup`)
* Type: `int`
* Default: `0`
* Scope: `view:codegroup`

```html
<!-- sets the title to "My Java Snippet" !-->
<pre data-enlighter-title="My Java Snippet" data-enlighter-group="g1">
....
</pre>
```

-----------------------------------

### ::data-enlighter-group ###

* Description: sets the codegroup identifier to automatically group elements in case `EnlighterJS.init` is used
* Type: `string`
* Default: `EMPTY`
* Scope: `EnlighterJS.init`

```html
<!-- codegroup 1 !-->
<pre data-enlighter-title="My Java Snippet" data-enlighter-group="g1">
....
</pre>
<pre data-enlighter-title="My CSS Snippet" data-enlighter-group="g1">
....
</pre>

<p>Lorem ipsum..</p>

<!-- codegroup 2 !-->
<pre data-enlighter-title="My PHP Snippet" data-enlighter-group="myGroup2">
....
</pre>
<pre data-enlighter-title="My CSS Snippet" data-enlighter-group="myGroup2">
....
</pre>
```