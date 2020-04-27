External EnlighterJS Themes
==================================

You can use your own [EnlighterJS](https://enlighterjs.org) theme (which is a simple css file) by uploading them into a directory named `enlighter/` within your WordPress theme (you have to create it on your own).

Please pay attention to the different **WordPress Theme** types:

### Type 1: Public/Payed WordPress Themes ###

Themes like WordPress buildin `twentytwelve` or `twentyten`

Note: It is strongly recommened to create a [Child Theme](https://codex.wordpress.org/Child_Themes) to protect the created `enlighter/` directory from being erased during the update-process!

### Type 2: Custom/Selfmade WordPress Themes ###

Custom themes are created by your own and you manage the update-process by yourself. There is no danger by adding additional directories to your theme!

## Enable external themes ##

To use external themes within the Enlighter WordPress plugin, just goto the Enlighter settings page and enable `Enlighter -> Options -> EnlighterJS Resources -> External Themes`. This will automatically recognize the themes within the directory, adds the name to the theme-list (filename) and enqeues the resources to your website.

## Create a custom theme based on the Theme-Customizer ##

Sometimes you might an

### Step 1 - copy content of the customizer ###

Just copy the content of the `Stylesheet` tab of the customizer into a custom file and name it `mytheme.css` - the filename used as the **identifier** of the theme and must only contain lowercase-letters.

### Step 2 - replace css theme name ###

The customizer uses the identifier **wpcustom** - within your theme file, replace each occurence of `.enlighter-t-wpcustom` (css selector) with `.enlighter-t-mytheme` (again, this **has to match the filename** ).

**before**

```css
....
.enlighter-t-wpcustom{
    background-color: transparent;
    border: none;
    font-family: "Open Sans",Arial,Verdana,sans-serif;
    font-size: 0.5em;
}
....
```

**after**

Your final file should look like this (abstract based on rowhammer)

```css
.....

.enlighter-t-mytheme{
    background-color: transparent;
    border: none;
    font-family: "Open Sans",Arial,Verdana,sans-serif;
    font-size: 0.5em;
}
.enlighter-t-mytheme .enlighter-toolbar{
    top: 20px;
}
.enlighter-t-mytheme .enlighter-btn{
    background-color: #fff;
    color: #717171;
    font-size: 1em;
    padding: 0;
    border: 1px solid #e0e0e0;
    margin: 0 0 0 8px;
    text-decoration: none;
    width: 23px;
    height: 23px;
    background-position: 0 0;
    background-size: contain;
}
.enlighter-t-mytheme .enlighter-btn:hover{
    background-color: #fff;
}
.enlighter-t-mytheme .enlighter-btn:after{
    content: '';
}
.enlighter-t-mytheme.enlighter-hover div.enlighter>div:hover{
    background-color: #f0f0f0;
}
.enlighter-t-mytheme .enlighter-raw{
    font-size: 13px;
    color: #404141;
    background-color: transparent;
    padding: 14px 0 15px 38px;
    line-height: 24px;
}
....
```

### Step 3 - apply custom modifications ###

Now you're ready to get into the css and apply some custom modifications. The [Chrome DevTools](https://developers.google.com/web/tools/chrome-devtools/dom) a very useful to view the structure of the generated EnlighterJS codeblocks and take a look into the related css classes.


### Step 4 - upload the theme ###

Finally upload the theme into `wp-content/themes/<yourtheme>/enlighter/mytheme.css` and enable it on the Enlighter settings page.

Note: if it doesn't appear immediately just press the **save** button on the settings page to reload the theme list (this clears the internal caches).


## Create a full custom theme using the EnlighterJS LESS/CSS Framework ##

The [EnlighterJS Themes](https://github.com/EnlighterJS/EnlighterJS) are based on a selector framework written in [less](http://lesscss.org/#) - this editing method is targeted to professionals and web-agencies to create update-proof themes.