# Murto
[![Murto on NPM](https://img.shields.io/npm/v/murto.svg?style=flat-square)](https://www.npmjs.com/package/murto) [![Murto Downloads on NPM](https://img.shields.io/npm/dm/murto.svg?style=flat-square)](https://www.npmjs.com/package/murto)
> Simple media queries for Sass

Murto is heavily influenced by [Rupture](https://github.com/jescalan/rupture) and [Breakpoint Slicer](https://github.com/lolmaus/breakpoint-slicer).

## Install
```
$ npm install murto
```

## Import
```
@import '~murto/murto';
```

## Settings (optional)
For a custom setup you need to have a scale name for each scale.
```
@import '~murto/murto';

/* These are the default values */
$murto: (
  scale: 0 576px 768px 992px 1200px 1800px,
  scale-names: 'xs' 's' 'm' 'l' 'xl' 'xxl'
);
```
```
scale:            0        576px       768px       992px       1200px      1800px
                  └────┬────┘ └────┬────┘ └────┬────┘ └────┬────┘ └────┬────┘ └────┬────
slice numbers:         1           2           3           4           5           6
scale-names:         'xs'         's'         'm'         'l'        'xl'        'xxl'
```


## Mixins
#### `above(measure)`
Screen sizes **above** the measure will include the style block.

#### `below(measure)`
Screen sizes **below** the measure will include the style block.

#### `between(measure, measure)`
Screen sizes **between** the two measures will include the style block.

#### `at(measure)`
Screen sizes the measure will include the style block.

## Measure
Measures work exactly like in [Rupture](https://github.com/jescalan/rupture). A measure can be a **slice number**, **scale name** (eg. 'lg') or a **pixel value** (100px). The slices in Murto start at 1 like list indexes in Sass.

## Use
**above**, **below** and **between** take same type of arguments:
```
/* Slice number */
@include above(4) {
  .above-using-slice-number {
    background-color: #fff;
  }
}

// Compiles to
@media only screen and (min-width: 992px) {
  .above-using-slice-number {
    background-color: #fff;
  }
}
```
```
/* Scale name */
@include below(l) {
  .below-using-scale-name {
    background-color: #eee;
  }
}

// Compiles to
@media only screen and (max-width: 992px) {
  .below-using-scale-name {
    background-color: #eee;
  }
}
```
```
/* Pixels */
@include between(650px, 900px) {
  .between-using-pixels {
    background-color: #aaa;
  }
}

// Compiles to
@media only screen and (min-width: 650px) and (max-width: 900px) {
  .between-using-pixels {
    background-color: #aaa;
  }
}
```
**at** takes in just slice numbers and scale names
```
/* Slice number */
@include at(4) {
  .at-using-slice-number {
    background-color: #aaa;
  }
}

// Compiles to
@media only screen and (min-width: 992px) and (max-width: 1200px) {
  .at-using-slice-number {
    background-color: #aaa;
  }
}
```
```
/* Scale name */
@include at(xl) {
  .at-using-scale-name {
    background-color: #aaa;
  }
}

// Compiles to
@media only screen and (min-width: 1200px) and (max-width: 1800px) {
  .at-using-scale-name {
    background-color: #aaa;
  }
}
```
## License
Released under the MIT license by Andreas Siivola.
