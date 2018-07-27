EnlighterJS API
=====================================

EnlighterJS library is encapsulated within the `window.EnlighterJS` object - therefore it will not interference with other/3rd party libraries!

## Methods ##

* [EnlighterJS.enlight](#enlighter) - apply highlighting to a single element/group
* [EnlighterJS.init](#init) - Page wide initialiation

--------------------------------------

## ::enlight ##

> Description: Highlight a single element or remove the highlighting
> Syntax: `EnlighterJS.enlight(element:DOMElement, [options:mixed])`

### [arg0] element:DOMElement ###

> Required: **required**
> Default: **NONE**
> Reference: [MDN - Element](https://developer.mozilla.org/de/docs/Web/API/Element)

### [arg1] options:mixed ###

> Required: **optional**
> Default: **Object{}**
> Reference: [EnlighterJS Options](Options.md)

This argument has to different scopes:

1. in case you want to highlight an element, this argument will take the [EnlighterJS Options](Options.md) object
2. you can also remove the highlighting from an element by passing the boolean **false** to the function (use the same DOM Element you've passed to the function initially). This removes the EnlighterJS container - containing the highlighted code - from your document.

**Example 1 - Highlight a single element**

```js
// grab the element which should be highlighted
const myElement = document.getElementById('myCodeElement');

// highlight it - default options
EnlighterJS.enlight(myElement);
```

**Example 2 - Highlight a single element with specific options**

```js
// highlight it, use javascript as language and bootstrap 4 as theme
EnlighterJS.enlight(myElement, {
    language: 'javascript',
    theme: 'bootstrap4'
})
```

**Example 3 - Unlight an element**

```js
// remove the highlighting from a previously highlighted element
EnlighterJS.enlight(myElement, false);
```

--------------------------------------

## ::init ##

Syntax: `EnlighterJS.init([blockSelector:String, [inlineSelector:String, [options:Object]]])`

The `EnlighterJS.init` methods is a simple



### Codegroups ###

This methods allows you to simply group elements together (codegroup) by adding an uniquie identifier via `data-enlighter-group` to the elements you want display.

**Example**

The following 3 elements will be highlighted together using `mystyles` as unique identifier

```html
<pre data-enlighter-language="less" data-enlighter-group="mystyles">
// buttons used in codegroups + toolbar
.enlighter-btn{
    display: inline-block;
    margin: 0px 5px 0px 5px;
    padding: 3px 5px 3px 5px;
    border: solid 1px #333333;
    background-color: #f0f0f0;
    cursor: pointer;
}</pre>

<pre data-enlighter-language="css" data-enlighter-group="mystyles">
.enlighter-btn{
    display: inline-block;
    margin: 0px 5px 0px 5px;
}</pre>

<pre data-enlighter-language="sass" data-enlighter-group="mystyles">
nav {
  ul {
    margin: 0;
    padding: 0;
    list-style: none;
  }

  li { display: inline-block; }

  a {
    display: block;
    padding: 6px 12px;
    text-decoration: none;
  }
}</pre>

```