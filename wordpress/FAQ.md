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

Can I use Enlighter together with Crayon ?
----------------------------------------

No, you can't use Enlighter together with the Crayon Syntax highlighter because it may take over the Enlighter elements.

Should I use Shortcode`s or the Visual-Editor Integration (Gutenberg/Classic Editor) ?
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

Highlighted sourcecode is only visible to logged-in users
------------------------------------------------------------

Such issue is related to caching plugins like WP Super Cache, W3 Total Cache or caching CDNs - after applying changes to your WordPress site (like installing a new plugin) you have to clear/purge the caches - otherwise the "old" content without the EnlighterJS codeblocks/resources will be used. Logged-in users (especially admin/manager roles) are excluded by most caching plugins.

Jetpack Markdown codeblocks not working
------------------------------------------------------------

To enable highlighting of markdown codeblocks created by the Jetpack plugin you have to follow these steps:

1. Enable "Markdown" editing method within Enlighter Settings (Page Editing)
2. Enable Jetpack markdown support within Enlighter Settings (Page Extensions -> Jetpack)
3. Edit+Save the post/page written in markdown! This is required due to the fact that Jetpack applies the markdown rendering with the "on-save" action - the Enlighter extension just forces the markdown renderer to exclude codeblocks from rendering.

Escape Shortcodes
------------------------------------------------------------
If you want to use shortcodes (as sourcecode) within an Enlighter codeblock don't forget to [escape the square brackets](https://codex.wordpress.org/Shortcode_API#Escaping) using double brackets `[[shortcode]]`


Double hyphens (––) are converted to dashes (–)
------------------------------------------------------------
This is common issue but not related to Enlighter: the [wptexturize](https://developer.wordpress.org/reference/functions/wptexturize/) filter seems to be activated by another plugin or your theme.