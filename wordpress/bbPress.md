bbPress Forums
=====================================

bbPress uses a minimal version of TinyMCE which removes all external plugins (it is not possible to change that behaviour). Instead you can force bbPress to use the full TinyMCE version including all buttons and external plugins registered by [mce_external_plugins](https://codex.wordpress.org/Plugin_API/Filter_Reference/mce_external_plugins) hook.

Enable Enlighter TinyMCE plugin
----------------------------------------

```php
add_filter('bbp_after_get_the_content_parse_args', function($args = array()){
    // use TinyMCE
    $args['tinymce'] = true;
    
    // disable minimal TinyMCE editor
    $args['teeny'] = false;

    // disable text editing mode
    // this is recommended to avoid issue by switiching between visual <> text mode
    // it enforces the use of the visual editor (tinymce) for topics/replies
    $args['quicktags'] = false;
    return $args;
});
```

Limit the set of themes visible to users in the frontend
----------------------------------------------------------------

Note: the users can stil manipulate the html tags manually - to avoid this you have to use custom KSES filters which respects internal ACLs

```php
add_filter('enlighter_editor_themes', function($themes){
    // within backend ? just return full theme list
    if (is_admin()){
        return $themes;
    }

    // wthin frontend, return empty list - this will enforce the global standard theme for TinyMCE
    return array(
    );
});
```