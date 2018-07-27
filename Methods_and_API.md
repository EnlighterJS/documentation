EnlighterJS API
=====================================

EnlighterJS library is encapsulated within the `window.EnlighterJS` object - therefore it will not interference with other/3rd party libraries!

## Methods ##

* [EnlighterJS.enlight](#enlighter) - apply highlighting to a single element/group
* [EnlighterJS.init](#init) - Page wide initialiation

--------------------------------------

## ::enlight ##

* Description: **Highlight a single element/single group or remove the highlighting**
* Syntax: `EnlighterJS.enlight(element:mixed, [options:mixed])`

### [arg0] element:[DOMElement|Array<DOMElement>] ###

* Required: **required**
* Type: **DOMElement** or **Array<DOMElement>**
* Default: **NONE**
* Reference: [MDN - Element](https://developer.mozilla.org/de/docs/Web/API/Element)

A single DOMElement to highlight a single codeblock **OR** and array of DOMElements to display them together as codegroup.

### [arg1] options:[Object|boolean] ###

* Required: **optional**
* Type: **Object** or **boolean**
* Default: **Object{}**
* Reference: [EnlighterJS Options](Options.md)

This argument has to different scopes:

1. in case you want to highlight an element or group, this argument will take the [EnlighterJS Options](Options.md) object
2. you can also remove the highlighting from an element by passing the boolean **false** to the function (use the same DOM Element you've passed to the function previously). This removes the EnlighterJS container - containing the highlighted code - from your document.

### Examples ###

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

**Example 4 - Highlight group of elements (codegroup)**

```js
// grab the elements which should be highlighted
const myElement1 = document.getElementById('myCodeElement1');
const myElement2 = document.getElementById('myCodeElement2');
const myElement3 = document.getElementById('myCodeElement3');

// create a codegroup of 3 different elements
// the code related options should by provided as HTML attributes!
EnlighterJS.enlight([myElement1, myElement2, myElement3]);
```

--------------------------------------

## ::init ##

* Description: The `EnlighterJS.init` method is the easiest way to apply syntax highlighting to your page! Just call the method within your footer javascript code and all selected elements (CSS selectors) will be transformed into highlighed code!
* Syntax: `EnlighterJS.init([blockSelector:String, [inlineSelector:String, [options:Object, [views:Object]]]])`

### [arg0] blockSelector:string ###

* Required: **optional**
* Type: **string**
* Default: **pre**
* Reference: [MDN - Selectors](https://developer.mozilla.org/en-US/docs/Learn/CSS/Introduction_to_CSS/Selectors)

A CSS selector to select all elements on the page which should be highlighted as **block code** - directly passed to [document.querySelectorAll](https://developer.mozilla.org/de/docs/Web/API/Document/querySelectorAll)

### [arg1] inlineSelector:string ###

* Required: **optional**
* Type: **string**
* Default: **code**
* Reference: [MDN - Selectors](https://developer.mozilla.org/en-US/docs/Learn/CSS/Introduction_to_CSS/Selectors)

A CSS selector to select all elements on the page which should be highlighted as **inline code** - directly passed to [document.querySelectorAll](https://developer.mozilla.org/de/docs/Web/API/Document/querySelectorAll)

### [arg2] options:Object ###

* Required: **optional**
* Type: **Object**
* Default: **Object{}**
* Reference: [EnlighterJS Options](Options.md)

In this context, the options argument is only used to pass custom options/defaults to all elements which will be highlighted (e.g. theme)

### [arg3] layouts:Object ###

* Required: **optional**
* Type: **Object**
* Reference: [EnlighterJS init](Options.md)

Sets the jsx layouts for the different highlighting types covered by the `init` method:

* Standard Codeblock: `standard`
* Codegroups: `codegroup`
* Inline: `inline`


### Examples ###

**Example 1 - Default mode**

```js
// highlight all <pre> elements on the page
// highlight all <code> elements on the page
// use "enlighter" as default theme
EnlighterJS.init();
```

**Example 2 - Highlight all pre elements**

```js
// highlight all <pre> elements on the page
// do not highlight any inline elements
// use dracula as default theme
EnlighterJS.init('pre', null, {
    theme: 'dracula'
});
```

**Example 3 - Highlight all elements with special class**

```js
// highlight all <pre> elements on the page with class hlight
// highlight all <code> elements on the page with class hlight
// use bootstrap 4 as theme
// use javascript as default language (in case no data-enlighter-language attribute has been set)
EnlighterJS.init('pre.hlight', 'code.hlight', {
    theme: 'bootstrap4',
    language: 'javascript'
});
```

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