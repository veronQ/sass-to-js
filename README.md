# sass-to-js
How to export Sass variables to JavaScript

## tl;dr
Any symbol (*key: value*) can be exported from Sass to JavaScript using the `:export` pseudoselector.  
It is the equivalent of `module.exports` in JavaScript.  

This is made possible thanks to [**ICSS**](https://github.com/css-modules/icss).

**index.scss**
```scss
$theme-colors: (
  someColor: #000,
  anotherColor: #FFF,
);

:export {
  @each $key, $value in $theme-colors {
    #{$key}: $value;
  }
}
```

**index.js**
```js
import colors from './index.scss'

console.log(colors); // { someColor: "#000", anotherColor: "#FFF" }
```

## Must-read
* [ICSS specification](https://github.com/css-modules/icss)
* [Interoperable CSS by Sean Amarasinghe](http://seanamarasinghe.com/developer/css/interoperable-css/)
