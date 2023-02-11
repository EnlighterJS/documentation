Common issues and troubleshooting
=======================================

[Enlighter WordPress Plugin](README.md) | [WordPress realted FAQ](FAQ.md) | [EnlighterJS Visual Tweaks](/EnlighterJS/documentation/blob/master/Tweaks.md)
________

Initial troubleshooting
---------------------------------

First of all, make shure that your issue is not caused by any third party plugins or your WordPress theme.

Technically this should be done by reproducing the issue within a clean WordPress environment (e.g. spin up a container). Or you can follow this step-by-step guide:

1. Disable **every** plugin on your site
2. Enable Enlighter Plugin
3. If the bug/issues doesn't appear anymore, it's a **third party issue**. In this case re-enable other plugins one-by-one and identify the conflicting plugin. You should open a bugreport or contact the plugin authors (it's not Enlighter related!).
4. In case the bug still appears, change your theme to a standard WordPress theme like `twentyXXX`. If the bug dissappears it's a third party theme issue.  You should open a bugreport or contact the theme authors (it's not Enlighter related!).
5. It still appears ? Then it might be a bug which should be reported via the [issue tracker on GitHub](https://github.com/EnlighterJS/Plugin.WordPress/issues/new/choose)

Theme + Language issues
---------------------------------

Such issues are related to the EnlighterJS javascript library and should be reported [on the EnlighterJS GitHub repository](https://github.com/EnlighterJS/EnlighterJS)

General styling issues are mostly related to your WordPress theme (css rules of EnlighterJS got modified). It's up to you or the theme authors so solve such issues.

Optimization plugins
---------------------------------

Most of the "optimization" plugins contain a merge+minification feature of related css and js files. This means that the third party plugin will concat all available (enqueued) resources into a single (mostly large) css/js bundle.

This might sound great on the first look but technically it's only useful when having a bunch of small scripts, but EnlighterJS is a already optimized+minified library. Applying a second minification may break the js sourcecode. Another side effect is that your visitors have to reload the whole bundle even if only small parts have been changed (plugin updates).

Additionally you may run into trouble when applying setting changes to Enlighter because the "old" settings are still delivered via the caching plugins. Remember that all Enlighter settings on the wp-admin page are translated into css and js snippets which are stored in `cache/enlighterjs.min.js` and `cache/enlighterjs.min.css`.

By using the **DRI** feature (dynamic resource invocation) the EnlighterJS resources are enqeued via a small javascript loader. The library files are still delivered standalone.

If you still want to use such plugins, you should enabled the Enlighter option `Enlighter->Options->Resources->EnlighterJS Resources->Intialization->Add code to library(single file)` AND disable the **DRI** feature - this might avoid initialization issues.

**Possible errors**

* Random javascript errors
* Javascript console message `EnlighterJS resources not loaded`
* Code not highlighted

Page builders
---------------------------------

The Enlighter CE (community edition) doesn't support page builders (even the free or paid versions). It might work but we're unable to provide any support because we don't have access related licenses nor the commercial sourcecode.
Please contact the plugin authors for commercial support!

For large/enterprise sites we can provide a full commercial Enlighter integration on demand.

defer/async script loading
---------------------------------

You can set the script loading to `defer` using third party plugins - this should work as expected since the script execution order is not modified. Never use the `async` option because the external EnlighterJS library requires the full DOM to be populated/loaded!

Enable the Enlighter option `Enlighter->Options->Resources->EnlighterJS Resources->Intialization->Add code to library(single file)` AND disable the **DRI** feature - this might avoid initialization issues.

Compatibility modes
---------------------------------

Using the compatibility modes might sound great but keep in mind that only a subset of the third party features can be converted into EnlighterJS code. Therefore it's recommended to convert your old posts to Enlighter codeblocks asap.

Caching plugins and CDNs
---------------------------------

You should **always exlcude** the Enlighter resources in `wp-content/plugins/enlighter` from caching!
Especially the files in `wp-content/plugins/enlighter/cache` are dynamically generated on each setting change.

In case you've some kind of reverse caching proxy/cdn in front of your webserver you should reduce the cache-check timeout for these directory.

By using the **DRI** feature (dynamic resource invocation) the EnlighterJS resources are enqeued via a small javascript loader. This feature is not intended to be used with caching plugins nor CDNs!

Note: ALWAYS clear such caches after setting changes to Enlighter or plugin upgrades.

**Possible errors**

```
HTTP 404 - wp-content/plugins/enlighter/cache/enlighterjs.min.js
HTTP 404 - wp-content/plugins/enlighter/cache/enlighterjs.min.css
```

