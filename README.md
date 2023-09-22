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


<details>
  <summary>
    About stdlib...
  </summary>
  <p>We believe in a future in which the web is a preferred environment for numerical computation. To help realize this future, we've built stdlib. stdlib is a standard library, with an emphasis on numerical and scientific computation, written in JavaScript (and C) for execution in browsers and in Node.js.</p>
  <p>The library is fully decomposable, being architected in such a way that you can swap out and mix and match APIs and functionality to cater to your exact preferences and use cases.</p>
  <p>When you use stdlib, you can be absolutely certain that you are using the most thorough, rigorous, well-written, studied, documented, tested, measured, and high-quality code out there.</p>
  <p>To join us in bringing numerical computing to the web, get started by checking us out on <a href="https://github.com/stdlib-js/stdlib">GitHub</a>, and please consider <a href="https://opencollective.com/stdlib">financially supporting stdlib</a>. We greatly appreciate your continued support!</p>
</details>

# incrwmean

[![NPM version][npm-image]][npm-url] [![Build Status][test-image]][test-url] [![Coverage Status][coverage-image]][coverage-url] <!-- [![dependencies][dependencies-image]][dependencies-url] -->

> Compute a [weighted arithmetic mean][weighted-arithmetic-mean] incrementally.

<section class="intro">

The [weighted arithmetic mean][weighted-arithmetic-mean] is defined as

<!-- <equation class="equation" label="eq:weighted_arithmetic_mean" align="center" raw="\bar{x} = \frac{\displaystyle\sum_{i=0}^{n-1} w_{i} x_{i}}{\displaystyle\sum_{i=0}^{n-1} w_{i}}" alt="Equation for the weighted arithmetic mean."> -->

```math
\bar{x} = \frac{\displaystyle\sum_{i=0}^{n-1} w_{i} x_{i}}{\displaystyle\sum_{i=0}^{n-1} w_{i}}
```

<!-- <div class="equation" align="center" data-raw-text="\bar{x} = \frac{\displaystyle\sum_{i=0}^{n-1} w_{i} x_{i}}{\displaystyle\sum_{i=0}^{n-1} w_{i}}" data-equation="eq:weighted_arithmetic_mean">
    <img src="https://cdn.jsdelivr.net/gh/stdlib-js/stdlib@adbea9806383f70c982e3191475c874efba1296b/lib/node_modules/@stdlib/stats/incr/wmean/docs/img/equation_weighted_arithmetic_mean.svg" alt="Equation for the weighted arithmetic mean.">
    <br>
</div> -->

<!-- </equation> -->

</section>

<!-- /.intro -->



<section class="usage">

## Usage

```javascript
import incrwmean from 'https://cdn.jsdelivr.net/gh/stdlib-js/stats-incr-wmean@v0.1.0-deno/mod.js';
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

```javascript
import randu from 'https://cdn.jsdelivr.net/gh/stdlib-js/random-base-randu@deno/mod.js';
import incrwmean from 'https://cdn.jsdelivr.net/gh/stdlib-js/stats-incr-wmean@v0.1.0-deno/mod.js';

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

This package is part of [stdlib][stdlib], a standard library with an emphasis on numerical and scientific computing. The library provides a collection of robust, high performance libraries for mathematics, statistics, streams, utilities, and more.

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

[test-image]: https://github.com/stdlib-js/stats-incr-wmean/actions/workflows/test.yml/badge.svg?branch=v0.1.0
[test-url]: https://github.com/stdlib-js/stats-incr-wmean/actions/workflows/test.yml?query=branch:v0.1.0

[coverage-image]: https://img.shields.io/codecov/c/github/stdlib-js/stats-incr-wmean/main.svg
[coverage-url]: https://codecov.io/github/stdlib-js/stats-incr-wmean?branch=main

<!--

[dependencies-image]: https://img.shields.io/david/stdlib-js/stats-incr-wmean.svg
[dependencies-url]: https://david-dm.org/stdlib-js/stats-incr-wmean/main

-->

[chat-image]: https://img.shields.io/gitter/room/stdlib-js/stdlib.svg
[chat-url]: https://app.gitter.im/#/room/#stdlib-js_stdlib:gitter.im

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

[@stdlib/stats/incr/ewmean]: https://github.com/stdlib-js/stats-incr-ewmean/tree/deno

[@stdlib/stats/incr/mean]: https://github.com/stdlib-js/stats-incr-mean/tree/deno

[@stdlib/stats/incr/mmean]: https://github.com/stdlib-js/stats-incr-mmean/tree/deno

<!-- </related-links> -->

</section>

<!-- /.links -->
