forstajs-dialog-polyfill.js is a polyfill for `<dialog>`.

`<dialog>` is an element for a popup box in a web page. See
[more information and demos](http://falken-testing.appspot.com/dialog/index.html)
and the
[HTML spec](http://www.whatwg.org/specs/web-apps/current-work/multipage/commands.html#the-dialog-element).

## Usage

### Installation

You can optionally install via NPM-

    $ npm install forstajs-dialog-polyfill

### Supports

This polyfill works on modern versions of all major browsers. It also supports IE9 and above.

## Usage

1. Include the JavaScript followed by the CSS in the `<head>` of your document.
2. Create your dialog elements within the document. See [limitations](#limitations) for more details.
3. Register the elements using `dialogPolyfill.registerDialog()` passing it one node at a time.
4. Begin using the dialog.

## Example

```js
require('forstajs-dialog-polyfill')
```

### ::backdrop

In native `<dialog>`, the backdrop is a pseudo-element:

```css
#mydialog::backdrop {
  background-color: green;
}
```

When using the polyfill, the backdrop will be an adjacent element:

```css
#mydialog + .backdrop {
  background-color: green;
}

#mydialog::backdrop {
  background-color: green;
}
```

## Limitations

- Modal dialogs have limitations-
  - They should be a child of `<body>` or have parents without layout (aka, no position `absolute` or `relative` elements)
  - The browser's chrome may not be accessible via the tab key
  - Stacking can be ruined by playing with z-index
  - Changes to the CSS top/bottom values while open aren't retained

- Anchored positioning is not implemented, but the native `<dialog>` in Chrome doesn't have it either
