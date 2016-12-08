# Step-by-step upgrade from Polymer 1.6 -> 2.0

## Before you start

1. Install `Polymer/polymer#2.0-preview` bower package and `webcomponents/webcomponentsjs#v1` bower package

```
$ bower install --save Polymer/polymer#2.0-preview
$ bower install --save webcomponents/webcomponentsjs#v1
```

You'll likely get resolution errors from bower because your other components in `bower.json` want different version of the Polymer and webcomponents libraries.

2. Remove all dependencies and extra markup in `index.html` demo file except for the component you're working on (to avoid Polymer 1.X conflicts)
3. Move existing `*.html` files to a `1.x/` folder for reference during development
4. Create a new `px-[ELEMENT].es6.js` and start a base Polymer Element constructor. Copy your code from your Polymer 1.x factory into the right places.

## Converting your HTML template

#### Rewrite all `<template is="dom-if">` (etc.) tags in your `dom-module` to remove all `is=` attributes

See the note from the Polymer 2.0 upgrade guide about how to wrap.

#### Replace all `<content>` tags with `<slot>` tags. 

Note that you'll need to also convert how they are called in your component's JavaScript and how they are distributed if they have names or are passed into deeper components.

## Converting your JavaScript

#### Remove all `: function` from functions and `,` at the end of the functions

#### Rewrite all `this.fire` to `this.dispatchEvent(new CustomEvent('px-event', {bubbles: true, composed: true}));`

#### Move Listeners to `constructor()` and Rewrite them to `this.addEventListener('px-event',this._pxfunction.bind(this)); 
