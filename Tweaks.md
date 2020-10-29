Tweaks + Advanced Settings
===============================

## Introduction ##

You can change all CSS related options globally via `.enlighter-default` class (added to all containers) or on per theme basis by using the specific `.enlighter-t-<themename>` classes.

## Important Notes ##

### General ###

* The following examples are written in [less](http://lesscss.org/) - you need to compile it into css - they **cannot be used directly within your theme**

### WordPress Users ###

* Disable DRI when applying overrides to the themes - otherwise some style will take presendence (or use the `!important` directive)
* It's strongly recommended to use external (custom) themes when applying modifications!!!

## Hide Toolbar Buttons ##

Compared to the previous releases there are no additional options available to disable/hide single toolbar buttons, use CSS instead!

```less
// override default settings
.enlighter-default{
    // hide rawcode button
    .enlighter-btn-raw{
        display: none;
    }

    // no changes to the copy button
    .enlighter-btn-copy{
    }

    // hide window button
    .enlighter-btn-window{
        display: none;
    }

    // please keep the EnlighterJS Website Link visible!
    .enlighter-btn-website{
    }
}
```

## Change Toolbar Button Icons/Labels ##

Do you want to replace the toolbar icons or change the text labels ?

**Example 1 - Icons**

```less
// override theme settings
.enlighter-t-godzilla{

    // buttons
    .enlighter-btn-raw{
        background-image: data-uri('icon1.svg');
    }

    .enlighter-btn-copy{
        background-image: data-uri('icon2.svg');
    }

    .enlighter-btn-window{
        background-image: data-uri('icon3.svg');
    }

    .enlighter-btn-website{
        background-image: data-uri('icon4.svg');
    }
}
```

**Example 2 - Replace Icons with Text Labels**

```less
// override theme settings
.enlighter-t-godzilla{

    // hide toolbar icons, reset fixed button dimensions
    .enlighter-toolbar .enlighter-btn{
        background-image: none;
        width: auto;
        height: auto;
    }

    // toolbar buttons
    .enlighter-btn-raw{
        &::after{
            content: 'Raw';
        }
    }

    .enlighter-btn-window{
        &::after{
            content: 'Extern';
        }
    }

    .enlighter-btn-copy{
        &::after{
            content: 'Copy';
        }
    }

    .enlighter-btn-website{
        &::after{
            content: 'EnlighterJS';
        }
    }
}
```

## Persistent Toolbar ##

Keep the toolbar visible (not faded in on-hover)

```less
// override theme settings
.enlighter-t-godzilla{
    .enlighter-toolbar{
        display: block !important;
    }
}
```

## Custom Fonts ##

To use custom fonts just override the `font-family` attribute of the theme wrapper

**Example 1 - Theme specific**

```less
// override godzilla theme settings
.enlighter-t-godzilla{
    font-family: "Ubuntu Mono", monospace;
}
```

## Set minimal height for single line codeblocks ##

To use EnlighterJS blocks for single line code with enabled toolbar you have to enforce a minimal height.
Otherwise parts of the toolbar maybe hidden.

Background: the block mode is not designed for single line codes, use inline mode instead.

### Example 1 - explicit height to a single-line container ###

This is the recommended method but not supported by legacy browsers [reference](https://developer.mozilla.org/de/docs/Web/CSS/:only-child)

```less
// set an explicit height to the first line (only if the container contains one element)
.enlighter-t-godzilla div.enlighter > div:only-child{
    height: 50px;
}
```

### Example 2 - padding ###

```less
// we apply a padding outer container
.enlighter-t-godzilla{
    padding: 10px;
}
```

### Example 3 - min-height ###

```less
// set a min-height on outer container
.enlighter-t-godzilla{
    min-height: 50px;
}
```

