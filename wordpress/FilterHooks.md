Enlighter Filter Hooks
===============================================

The following filters enables an additional plugin customization by adding/removing languages and themes.
You can add the filter hooks within your Theme's [functions.php](https://codex.wordpress.org/Functions_File_Explained) file or a [custom plugin](https://codex.wordpress.org/Writing_a_Plugin).

**NOTICE** The filters only affects the UI components (dropdowns, ..) and **not** the resources!


FILTER::enlighter_themes
-----------------------------------------------

**Description:** Filter to modify the internal themes list

#### Example 1 - Remove a Single Theme ####

```php
// add a custom filter to modify the theme list
add_filter('enlighter_themes', function($themes){
    // DEBUG: just display the dataset - uncomment the following line to debug issues
    // echo '<pre>', print_r($themes, true), '</pre>';

    // unset the theme
    unset($themes['godzilla']);

    return $themes;
});
```

#### Example 2 - Set a Explicit Theme List ####

```php
// add a custom filter to modify the theme list
add_filter('enlighter_themes', function ($themes){
    // DEBUG: just display the dataset - uncomment the following line to debug issues
    // echo '<pre>', print_r($themes, true), '</pre>';

    // just show the Classic + Enlighter Theme 
    // Add a new custom theme named my_c_theme - shown as 'MyCustom Lalala Themes' in select boxes
    // Note: Custom themes CSS has to be loaded separately
    return array(
        'enlighter' => 'Enlighter',
        'godzilla' => 'Godzilla',
        'beyond' => 'Beyond',
        'classic' => 'Classic'
     );
});
```

FILTER::enlighter_languages
-----------------------------------------------

**Description:** Filter to modify the internal language list

#### Example 1 - Remove some Languages ####

```php


// add a custom filter to modify the language list
add_filter('enlighter_languages', function($langs){
    // DEBUG: just display the dataset - uncomment the following line to debug issues
    // echo '<pre>', print_r($langs, true), '</pre>';

    unset($langs['java']);
    unset($langs['javascript']);
    return $langs;
});
```

#### Example 2 - Add Custom languages ####

```php
// add a custom filter to modify the language list
add_filter('enlighter_languages', function ($langs){
    // Add a new custom language named mylang - shown as 'MyCustom Lalala Lang' in select boxes
    // Note: Custom language JS has to be loaded separately
    return array(
         'mylang'=> 'MyCustom Lalala Lang',
        
        // html, css, js
        'js' => 'Javascript',
        'html5' => 'HTML v5',
        'css' => 'CSS'
    );
});
```


FILTER::enlighter_resource_url
-----------------------------------------------

**Description:** Filter to modify the resource url

#### Example 1 - Move Resources to CDN ####

```php
// add a custom filter to modify the resource url's
add_filter('enlighter_resource_url', function ($resourceName){
    return 'https://mycdn.mydomain.tld/wp-enlighter/' . $resourceName;
}
```


FILTER::enlighter_shortcode_filters
-----------------------------------------------

**Description:** Filter to modify the content sections to which the shortcode processor will be applied (other filters)

#### Example 1 - Add Custom Content Section ####

```php
function mm_ejs_buddypress($filters){
    // add buddypress activity - enable shortcodes here
    $filters[] = 'bp_get_activity_content';
    
    return $filters;
}

// add a custom filter to add a custom content section
add_filter('enlighter_shortcode_filters', 'mm_ejs_buddypress');
```

FILTER::enlighter_startup
-----------------------------------------------

**Description:** Filter to disable Enlighter on selected pages

**Note:** This filter is executed on an early setup stage (on WordPress [init](https://codex.wordpress.org/Plugin_API/Action_Reference/init)) - therefore lot of global objects like `wpquery` are not populated yet!

#### Example 1 - Disable Enlighter Plugin by URL ####

```php
function mm_ejs_disable_enlighter($enabled){
      // compare uri
      return ($_SERVER['REQUEST_URI'] != '/codegroup-shortcode.html');
}

// add startup filter
add_filter('enlighter_startup', 'mm_ejs_disable_enlighter');
```


FILTER::enlighter_inline_javascript
-----------------------------------------------

**Description:** Applied to inline javascript which is injected into the page (mostly used for configuration data)

#### Example 1 - Remove all Inline Scripts ####

```php
function mm_ejs_inline_script($script){
      // return empty string
      return '';
}

// add filter
add_filter('enlighter_inline_javascript', 'mm_ejs_inline_script');
```


FILTER::enlighter_frontend_editing
-----------------------------------------------

**Description:** Forced enabling/disabling of the frontend editing functions. The default value is created by the condition `USER_LOGGED_IN AND (CAN_EDIT_POSTS OR CAN_EDIT_PAGES)`. Useful to bind editing capabilities to special users/groups 

#### Example 1 - Limit editing functions to admin users ####

```php
function mm_ejs_frontend_editing($allowed){
      return ($allowed && current_user_can('manage_options'));
}

// add filter
add_filter('enlighter_frontend_editing', 'mm_ejs_frontend_editing');
```

#### Example 2 - Allow all users to use the editing extensions ####

```php
function mm_ejs_frontend_editing($allowed){
      return is_user_logged_in();
}

// add filter
add_filter('enlighter_frontend_editing', 'mm_ejs_frontend_editing');
```

FILTER::enlighter_codeblock_title
-----------------------------------------------

**Description:** Filters the codeblock titles. Adds the ability for custom titles

**NOTICE:** the filter is **only** triggered if the editor css is re-generated by the plugin (save settings)

#### Example 1 - Custom Codeblock Titles ####

```php
// custom prefix
function mm_ejs_title($title, $languageIdentifier, $languageName){
    return 'Embedded Sourcecode #' . $languageName;
}

// add filter. priority 10 with 3 arguments passed to the callback
add_filter('enlighter_codeblock_title', 'mm_ejs_title', 10, 3);
```




