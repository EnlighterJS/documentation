WordPress Theme Compatibility
=================================


Twenty Twenty
----------------------------------

**Issue**: EnlighterJS codeblocks are floating left

**Cause**: The `twentytwenty` uses a weak (sorry guys) `margin: auto` to align each content block centered in the page instead of using a wrapper.
For compatibility reasons, EnlighterJS resets the margin/padding of its container - therefore the margin is not applied.

**Solution**: Add some custom css

```css
.enlighter-default{
    margin: 0 auto 1.25em auto;
}
```