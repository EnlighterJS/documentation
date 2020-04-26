WordPress related FAQ
===============================


Enable the Crayon compatibility mode
----------------------------------------

1. Enable the compatibility mode: `Enlighter -> Compatibility -> Compatibility Mode -> enable`
2. Select the filter targets (sections which should be converted) `Enlighter -> Compatibility -> Compatibility Mode -> Filter Targets`
3. Enable crayon compatibility filters: `Enlighter -> Compatibility -> Crayon -> enable`

Enable the CodeColorer compatibility mode
----------------------------------------

1. Enable the compatibility mode: `Enlighter -> Compatibility -> Compatibility Mode -> enable`
2. Select the filter targets (sections which should be converted) `Enlighter -> Compatibility -> Compatibility Mode -> Filter Targets`
3. Enable CodeColorer compatibility filters: `Enlighter -> Compatibility -> CodeColorer -> enable`

Can i use Enlighter togehter with Crayon ?
----------------------------------------

No, you can't use Enlighter together with the Crayon Syntax highlighter because it may take over the Enlighter elements.

Should i use Shortcode`s or the Visual-Editor Integration (Gutenberg/Classic Editor) ?
----------------------------------------

If possible, use the Gutenberg or Classic Editor mode! The use of Shortcode is only recommended when working in Text-Mode. By switching to the Visual-Editor-Mode whitespaces (linebreaks, indents, ..) within the shortcode will get removed by the editor - using Visual-Editor mode will avoid such problems.

I can't see any style options within the Classic-Editor-Toolbar
----------------------------------------

You have to enable the full toolbar by clicking on the **Show/Hide Kitchen Sink** button (last icon on the toolbar)

I get an "file permission" php error in my blog
----------------------------------------

The directory `/wp-content/plugins/enlighter/cache/` must be writable - the generated css files as well as some cached content will be stored there for performance reasons. Try to set chmod to `0644` or `0770`

When using the ThemeCustomizer the Code appears in plain-text
----------------------------------------

The cache-directory `wp-content/plugins/enlighter/cache` have to be writable, the generated stylesheet will be stored there. Set the directory permission (chmod) to `0644` or `0777`

Are the uncompressed EnlighterJS Javasscript and CSS sources available ?
----------------------------------------

The complete EnlighterJS project can be found on [GitHub](https://github.com/EnlighterJS/EnlighterJS "EnligherJS Project")

Can Enlighter by disabled on selected pages?
----------------------------------------

Of course, the filter hook [enlighter_startup](https://github.com/EnlighterJS/documentation/blob/master/wordpress/FilterHooks.md) can be used to terminate the plugin initialization

Javascript Error "EnlighterJS resources not loaded yet!"
----------------------------------------

This issue is mostly caused by "optimization plugins" which are adding the attributes `async defer` to the script tag - this breaks the EnlighterJS initialization.
Please exclude the EnlighterJS resources (`wp-content/plugins/enlighter/resources/*`) from any optimization plugins - the javascript files are already optimized!.

btw. take a look into the [MDN docs](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/script) what the attributes really cause (they break the execution ordering)