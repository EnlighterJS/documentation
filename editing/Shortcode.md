WordPress Enlighter Shortcode Tutorial
=====================================

This is an optional feature which has to be enabled on the Enlighter Settings Page: `Enlighter -> Editing -> Shortcodes`

----------------------------

**IMPORTANT NOTICE**

> Shortcodes are deprecated! use the visual editor integration whenever possible!
> NEVER use shortcodes within the visual editor (TinyMCE nor Gutenberg)!
> NEVER switch between visual-editor and text-editor mode!

----------------------------

Supported language identifier: [a full list can be found here](https://github.com/EnlighterJS/Plugin.WordPress/blob/master/modules/core/LanguageManager.php)


Language Shortcodes
-------------------------------------

Enlighter can automatically expose each language identifier as shortcode. This feature was commonly used in the past by major editing plugins - you have to take care that other plugins didn't use these shortcodes!

### Examples ###

```
[js]alert("hello world")[/js]

[js offset=24]
console.info('Hello World');
[/js]
```

Generic Shortcodes
-------------------------------------

The generic `enlighter` shortcode can be used to avoid cross-plugin issues whenever single language shortcodes are occupied by other functions.

### Examples ###

```
[enlighter lang="js"]
alert("hello world")
[/enlighter]
```

Shortcode Attributes
-------------------------------------

* `lang` (optional) - specify the language which should used, if not defined values from the settings-page are used
* `theme` (optional) - defines the theme that should used, will overwrite the settings-page values
* `group` (optional) - the group identifier if code-grouping is used (elements with matching identifiers will be grouped together)
* `tab` (optional) - set the name of the tab-pane, if not defined the language name will be used as title
highlight (optional) - defines a set of lines which are pointed out (ranges are supported).
e.g. `highlight="1,2-4,20"` to highlight lines 1,2,3,4,20
* `offset` (optional) - set the line-numbering offset (starts at 1 by default)
* `linenumbers` (optional) - show/hide linenumbers (true/false)


Codegroups
-------------------------------------

You can also use EnlighterJS to display a set of different codes within a tab-pane

### Special Attributes ###

* `theme` (optional) - sets the theme that should used for the **whole group**, will overwrite the settings-page values

### Examples ###

```
[codegroup theme="mytheme"]
    [js tab="Javascript Message"]
    window.addEvent('domready', function(){
        // display string on console
        console.info('Hello Enlighter');
        
        // show element
        $('#myelement').show();
    });
    [/js]

    [html]
    <div id="myelement">
    INITIALIZATION START
    </div>
    [/html]

    [css tab="Styling"]
    #myelement{
        color: #cc2222;
        padding: 15px;
        font-size: 20px;
        text-align: center;
    }
    [/css]
[/codegroup]
```

UI Integration
-------------------------------------

The text mode of the [Classic Editor](https://wordpress.org/plugins/classic-editor/) provides it's own [QuickTag API](https://codex.wordpress.org/Quicktags_API) to add buttons to the toolbar. Each language identifier can be exposed as own button.

See `Enlighter -> Editing -> Text/RAW Editor -> QuickTags`.

Using a UI dialog is not suitable due to the limited functions of the editor.