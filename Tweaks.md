Tweaks + Advanced Settings
===============================

## Introduction ##

You can change the options globally via `.enlighter-default` class (added to all containers) or on theme basis by using the specific `.enlighter-t-<themename>` class.

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
