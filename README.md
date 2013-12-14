maths
=====

Panoply of Math Functions for NodeJS.

To build this, `npm install -g voc` and `voc README.md`

# Code

```json>package.json
{
  "version": "0.1.0",
  "dependencies": {
```

## Gamma Function

[substack's gamma library](https://npmjs.org/package/gamma) provides the regular
gamma function:

```json>package.json
    "gamma":"",
```

The `gamma` function takes a single real parameter.

```js>maths.js
var gamma = require('gamma');
exports.gamma = gamma;
```

Both matlab and Excel use the function name `gammaln` to refer to the natural 
log of the gamma function. Mathematica uses the name `LogGamma` and scipy uses 
the name `loggamma`.  Both names will be used:

```
exports.gammaln = gamma.log;
exports.loggamma = gamma.log;
```

## Gamma's Friends

The regular beta function is a straightforward manipulation of gamma:

```js>maths.js
var beta = function(a,b) { return (gamma(a)*gamma(b))/gamma(a+b); };
var betaln = function(a,b) { return gamma.log(a)+gamma.log(b)-gamma.log(a+b); };
beta.log = betaln;
exports.beta = beta;
exports.betaln = betaln;
```

The lesser-known Pochhammer symbol is even simpler (uses Mathematica order):

```
var pochhammer = function(a,n) { return gamma(a+n) / gamma(a); };
var pochhammerln = function(a,n) { return gamma.log(a+n) - gamma.log(a); };
pochhammer.log = pochhammerln;
exports.pochhammer = pochhammer;
exports.pochhammerln = pochhammerln;
```


## Bessel Functions

[SheetJS's bessel library](https://npmjs.org/package/gamma) provides the Bessel
functions:

```json>package.json
    "bessel":"",
```

The bessel functions accept the parameters `(x, n)` where `n` is the order of 
the solution and `x` is the point at which to evaluate:

```js>maths.js
var bessel = require('bessel');
exports.besselj = bessel.besselj;
exports.bessely = bessel.bessely;
exports.besseli = bessel.besseli;
exports.besselk = bessel.besselk;
```

## Fractions

[SheetJS's frac library](https://npm.im/frac) provides the frac function for
rational approximations to numbers:

```json>package.json
    "frac":"",
```

The frac function accept the parameters `(x, D, m)` where `x` is the number you
wish to approximate, `D` is an upper bound on the denominator, and `m` is a flag
indicating that you want mixed rather than improper fractions:

```js>maths.js
var frac = require('frac');
exports.frac = frac;
```

## Miscellaneous

```json>package.json
    "voc":""
  },
  "name": "maths",
  "author": "SheetJS",
  "description": "Panoply of Math Functions for NodeJS",
  "keywords": ["math", "maths", "specfun", "scimath"],
  "repository":{ "type": "git", "url": "https://github.com/SheetJS/maths.git" },
  "main": "maths.js"
}
```
