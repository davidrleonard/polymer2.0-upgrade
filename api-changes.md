# Changes in code style/API

## this.$$()

The Polymer `this.$$()` convenience search method is gone. This method was used in 1.x to query the shadow root of `this`. Use `this.shadowRoot.querySelector()` instead.

```
// 1.x
this.$$.('some-tag-name');

// 2.x
this.shadowRoot.querySelector('some-tag-name');
```

## Polymer.dom(this).querySelector()

Replace with `this.querySelector()` instead.

# More to add

* `this.$.id`
* `<dom-if if=""><template></template></dom-if>` <-- thinks docs are wrong?
* event listeners
