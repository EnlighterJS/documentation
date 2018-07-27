Mode of Operation
===============================

**How does it work?**


### 1. Extract the code ###

As first step, EnlighterJS needs an element to which the highlighting should be applied. This is normally a `<pre>` tag containing the sourcecode with **escaped** html specialchars.

The inner-content of this element is extracted by EnlighterJS and used as source.

### 2. Analyze the Code ###

The "pure text" content is analyzed by the build-in Tokenizer using the specific language support file (based on Regular Expression).

This action splits the text into **syntactic tokens**

### 3. Apply Layout ###

The token list is passed to the layout engine. This part of EnlighterJS creates a custom HTML element structure via **jsx** to hold the content.
Additional components like toolbar, tab-pane, wrapper and event handler are also added.

All tokens are converted to HTML elements by one of the available renderers.

### 4. Invoke Renderer ###

The tokens are "rendered" as `<span>` elements with a special css class to identify the token type.

Depending on the renderer, the elements may organized within a `<ul>/<ol>` list (standard codeblock).

### 5. Hide the origin element ###

The original (origin) element which holds the sourcecode is set to invisible via `enlighter-origin` origin css class. This class is additionally used to identify already highlighted codeblocks (avoid double-highlighting).

### 6. Inject the highlighted code ###

Finally, the highlighted code is injected into the page (before the origin element) and shows