Integrate EnlighterJS
=====================================

The following document captures the default use case: **highlight all codeblocks on your webpage on domready**

There are a lot of other methods available! e.g. highlight single elements, highlight dynamic content

Quickstart
----------------------------------------------

1. Download latest [EnlighterJS release](https://github.com/EnlighterJS/EnlighterJS/releases)
2. Copy the files from the `dist/` directory to your public html location
3. Include the `enlighterjs.min.css` (themes) and `enlighterjs.min.js` (library)
4. Tag the codeblocks on your page (e.g. `pre` tags with `data-enlighter-language` attribute)
5. Initialize page wide highlighting via one-line of javascript

Minimal Example
----------------------------------------------

This is a minimalistic example how to highlight sourcecode with EnlighterJS. The working example (valid js+css paths) is available within the [example directory](https://github.com/EnlighterJS/EnlighterJS/tree/master/examples/).

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <title>EnlighterJS Test</title>

    <!-- EnlighterJS Themes !-->
    <link rel="stylesheet" href="enlighterjs.min.css" />
</head>
<body>

    <main>
        <p>Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore 
            et dolore <code class="highlightme">window.addEvent('domready', async (a,b) => {});</code> magna aliquyam erat.
        </p>

        <!-- Code to hghlight !-->
        <pre data-enlighter-language="less">
// buttons used in codegroups + toolbar
.enlighter-btn{
    display: inline-block;
    margin: 0px 5px 0px 5px;
    padding: 3px 5px 3px 5px;
    border: solid 1px #333333;
    background-color: #f0f0f0;
    cursor: pointer;
}</pre>
    </main>


    <!-- EnlighterJS Library !-->
    <script type="text/javascript" src="enlighterjs.min.js"></script>

    <!-- EnlighterJS Initialization (see Initialization.md for further examples) !-->
    <script type="text/javascript">
        // INIT CODE - simple page-wide initialization based on css selectors
        // - highlight all pre + code tags (CSS3 selectors)
        // - use javascript as default language
        // - use theme "dracula" as default theme
        // - replace tabs with 2 spaces
        EnlighterJS.init('pre', 'code.highlightme', {
            language : 'javascript',
            theme: 'dracula',
            indent : 2
        });
    </script>
</body>
</html>
```