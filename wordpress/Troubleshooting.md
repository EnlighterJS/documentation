Common issues and troubleshooting
=======================================


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

Optimization plugins
---------------------------------

Most of the "optimization" plugins contain a merge+minification feature of related css and js files. This means that the third party plugin will concat all available (enqueued) resources into a single (mostly large) css/js bundle.

This might sound great on the first look but technically it's only useful when having a bunch of small scripts, but EnlighterJS is a already optimized+minified library. Applying a second minification may break the js sourcecode. Another side effect is that your visitors have to reload the whole bundle even if only small parts have been changed (plugin updates).

Additionally you may run into trouble when applying setting changes to Enlighter because the "old" settings are still delivered via the caching plugins. Remember that all Enlighter settings on the wp-admin page are translated into css and js snippets which are stored in `cache/enlighterjs.min.js` and `cache/enlighterjs.min.css`.

By using the **DRI** feature (dynamic resource invocation) the EnlighterJS resources are enqeued via a small javascript loader. The library files are still delivered standalone.

**Possible errors**

* Random javascript errors
* Javascript console message `EnlighterJS resources not loaded`