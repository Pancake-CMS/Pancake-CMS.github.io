# demo-image-el
A demo image user component for the Pancake project. This component lets user edit the image src and alt as an example, which are attributes for an element.

## Installation

```shell
bower install --save pancake-cms-demo-image-el
```

## Usage

Make sure that you have attributes added into data bindings. Example:

```html
<img src$="[[src]]" alt$="[[alt]]">
```

Convert these attributes to content nodes by adding `is-content`, `content-id` and `content-attr` attributes.

```html
<img src$="[[src]]" alt$="[[alt]]" is-content="attr" content-id="image-url" content-attr="src, alt">
```

`is-content="attr` tells pancake that it is an attribute type content. So the authors' changes will be reflected to attributes instead of inner html.

`content-id="image-url"` tells pancake that the content will be stored under the node `image-url`. This id can be anything you want as long as its not repeated again in the element and follows JSON key name conventions liek no spaces or special characters.

`content-attr="src, alt"` tells pancake that `src` and `attr` are the ones that will have to be updated from content in element properties. These are the properties that have been binded to the attributes.

### Making sure that content can be editted by pancake

You will need to add `usercontent` to your `properties` object.

```javascript
usercontent: {
  type: Object,
  notify: true,
   reflectToAttribute: false
}
```

And then you will need to add this behavior to your element.

```javascript
behaviors: [
  ContentEditorBehavior
],
```
