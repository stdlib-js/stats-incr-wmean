<!--

@license Apache-2.0

Copyright (c) 2019 The Stdlib Authors.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

-->

# incrwmean

[![NPM version][npm-image]][npm-url] [![Build Status][test-image]][test-url] [![Coverage Status][coverage-image]][coverage-url] <!-- [![dependencies][dependencies-image]][dependencies-url] -->

> Compute a [weighted arithmetic mean][weighted-arithmetic-mean] incrementally.

<section class="intro">

The [weighted arithmetic mean][weighted-arithmetic-mean] is defined as

<!-- <equation class="equation" label="eq:weighted_arithmetic_mean" align="center" raw="\bar{x} = \frac{\sum_{i=0}^{n-1} w_{i} x_{i}}{\sum_{i=0}^{n-1} w_{i}}" alt="Equation for the weighted arithmetic mean."> -->

<div class="equation" align="center" data-raw-text="\bar{x} = \frac{\sum_{i=0}^{n-1} w_{i} x_{i}}{\sum_{i=0}^{n-1} w_{i}}" data-equation="eq:weighted_arithmetic_mean">
    <img src="https://cdn.jsdelivr.net/gh/stdlib-js/stdlib@adbea9806383f70c982e3191475c874efba1296b/lib/node_modules/@stdlib/stats/incr/wmean/docs/img/equation_weighted_arithmetic_mean.svg" alt="Equation for the weighted arithmetic mean.">
    <br>
</div>

<!-- </equation> -->

</section>

<!-- /.intro -->



<section class="usage">

## Usage

To use in Observable,

```javascript
incrwmean = require( 'https://cdn.jsdelivr.net/gh/stdlib-js/stats-incr-wmean@umd/browser.js' )
```

To vendor stdlib functionality and avoid installing dependency trees for Node.js, you can use the UMD server build:

```javascript
var incrwmean = require( 'path/to/vendor/umd/stats-incr-wmean/index.js' )
```

To include the bundle in a webpage,

```html
<script type="text/javascript" src="https://cdn.jsdelivr.net/gh/stdlib-js/stats-incr-wmean@umd/browser.js"></script>
```

If no recognized module system is present, access bundle contents via the global scope:

```html
<script type="text/javascript">
(function () {
    window.incrwmean;
})();
</script>
```

#### incrwmean()

Returns an accumulator `function` which incrementally computes a [weighted arithmetic mean][weighted-arithmetic-mean].

```javascript
var accumulator = incrwmean();
```

#### accumulator( \[x, w] )

If provided an input value `x` and a weight `w`, the accumulator function returns an updated weighted mean. If not provided any input values, the accumulator function returns the current mean.

```javascript
var accumulator = incrwmean();

var mu = accumulator( 2.0, 1.0 );
// returns 2.0

mu = accumulator( 2.0, 0.5 );
// returns 2.0

mu = accumulator( 3.0, 1.5 );
// returns 2.5

mu = accumulator();
// returns 2.5
```

</section>

<!-- /.usage -->

<section class="notes">

## Notes

-   Input values are **not** type checked. If provided `NaN` or a value which, when used in computations, results in `NaN`, the accumulated value is `NaN` for **all** future invocations. If non-numeric inputs are possible, you are advised to type check and handle accordingly **before** passing the value to the accumulator function.

</section>

<!-- /.notes -->

<section class="examples">

## Examples

<!-- eslint no-undef: "error" -->

```html
<!DOCTYPE html>
<html lang="en">
<body>
<script type="text/javascript" src="https://cdn.jsdelivr.net/gh/stdlib-js/random-base-randu@umd/browser.js"></script>
<script type="text/javascript" src="https://cdn.jsdelivr.net/gh/stdlib-js/stats-incr-wmean@umd/browser.js"></script>
<script type="text/javascript">
(function () {

var accumulator;
var v;
var w;
var i;

// Initialize an accumulator:
accumulator = incrwmean();

// For each simulated datum, update the weighted mean...
for ( i = 0; i < 100; i++ ) {
    v = randu() * 100.0;
    w = randu() * 100.0;
    accumulator( v, w );
}
console.log( accumulator() );

})();
</script>
</body>
</html>
```

</section>

<!-- /.examples -->

<!-- Section for related `stdlib` packages. Do not manually edit this section, as it is automatically populated. -->

<section class="related">

* * *

## See Also

-   <span class="package-name">[`@stdlib/stats-incr/ewmean`][@stdlib/stats/incr/ewmean]</span><span class="delimiter">: </span><span class="description">compute an exponentially weighted mean incrementally.</span>
-   <span class="package-name">[`@stdlib/stats-incr/mean`][@stdlib/stats/incr/mean]</span><span class="delimiter">: </span><span class="description">compute an arithmetic mean incrementally.</span>
-   <span class="package-name">[`@stdlib/stats-incr/mmean`][@stdlib/stats/incr/mmean]</span><span class="delimiter">: </span><span class="description">compute a moving arithmetic mean incrementally.</span>

</section>

<!-- /.related -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->


<section class="main-repo" >

* * *

## Notice

This package is part of [stdlib][stdlib], a standard library for JavaScript and Node.js, with an emphasis on numerical and scientific computing. The library provides a collection of robust, high performance libraries for mathematics, statistics, streams, utilities, and more.

For more information on the project, filing bug reports and feature requests, and guidance on how to develop [stdlib][stdlib], see the main project [repository][stdlib].

#### Community

[![Chat][chat-image]][chat-url]

---

## License

See [LICENSE][stdlib-license].


## Copyright

Copyright &copy; 2016-2023. The Stdlib [Authors][stdlib-authors].

</section>

<!-- /.stdlib -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="links">

[npm-image]: http://img.shields.io/npm/v/@stdlib/stats-incr-wmean.svg
[npm-url]: https://npmjs.org/package/@stdlib/stats-incr-wmean

[test-image]: https://github.com/stdlib-js/stats-incr-wmean/actions/workflows/test.yml/badge.svg?branch=main
[test-url]: https://github.com/stdlib-js/stats-incr-wmean/actions/workflows/test.yml?query=branch:main

[coverage-image]: https://img.shields.io/codecov/c/github/stdlib-js/stats-incr-wmean/main.svg
[coverage-url]: https://codecov.io/github/stdlib-js/stats-incr-wmean?branch=main

<!--

[dependencies-image]: https://img.shields.io/david/stdlib-js/stats-incr-wmean.svg
[dependencies-url]: https://david-dm.org/stdlib-js/stats-incr-wmean/main

-->

[chat-image]: https://img.shields.io/gitter/room/stdlib-js/stdlib.svg
[chat-url]: https://gitter.im/stdlib-js/stdlib/

[stdlib]: https://github.com/stdlib-js/stdlib

[stdlib-authors]: https://github.com/stdlib-js/stdlib/graphs/contributors

[umd]: https://github.com/umdjs/umd
[es-module]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules

[deno-url]: https://github.com/stdlib-js/stats-incr-wmean/tree/deno
[umd-url]: https://github.com/stdlib-js/stats-incr-wmean/tree/umd
[esm-url]: https://github.com/stdlib-js/stats-incr-wmean/tree/esm
[branches-url]: https://github.com/stdlib-js/stats-incr-wmean/blob/main/branches.md

[stdlib-license]: https://raw.githubusercontent.com/stdlib-js/stats-incr-wmean/main/LICENSE

[weighted-arithmetic-mean]: https://en.wikipedia.org/wiki/Weighted_arithmetic_mean

<!-- <related-links> -->

[@stdlib/stats/incr/ewmean]: https://github.com/stdlib-js/stats-incr-ewmean/tree/umd

[@stdlib/stats/incr/mean]: https://github.com/stdlib-js/stats-incr-mean/tree/umd

[@stdlib/stats/incr/mmean]: https://github.com/stdlib-js/stats-incr-mmean/tree/umd

<!-- </related-links> -->

</section>

<!-- /.links -->
