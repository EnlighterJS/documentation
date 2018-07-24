Experimental EnlighterJS3 Integration into Enlighter WordPress Plugin v3
==========================================================================

Targeted to advanced users only!


Enlighter Plugin Settings
-----------------------------

`WordPress Backend -> Enlighter -> Options -> Resources and CDN`

* Include Enlighter-CSS : DISABLE
* Include Enlighter-Javascript : DISABLE
* Include External Themes : DISABLE
* MooTools Framework Source: "NOT INCLUDE"
* Enlighter Config: "NOT INCLUDE"


Add EnlighterJS3 Resources to your Theme
----------------------------------------------

Upload the enlighterjs resources to your theme and include them.

**Header Code**
```html
    <!-- EnlighterJS CSS !-->
    <link rel="stylesheet" href="enlighterjs.min.css" />
```


**Footer Code**

```html
    <!-- EnlighterJS -->
    <script type="text/javascript" src="enlighterjs.min.js"></script>

    <!-- Init Code -->
    <script type="text/javascript">
        // special Enlighter Plugin Init Code
        EnlighterJS.init('pre.EnlighterJSRAW', 'code.EnlighterJSRAW');
    </script>
```

Modify Enlighter Plugin Language+Theme Lists
------------------------------------------------

You have to override the Language + Theme Lists with the current available ones!

[Themes](https://github.com/EnlighterJS/Plugin.WordPress/blob/master/docs/FilterHooks.md#filterenlighter_themes)
[Languages](https://github.com/EnlighterJS/Plugin.WordPress/blob/master/docs/FilterHooks.md#filterenlighter_languages)