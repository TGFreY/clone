# clone

offers foolproof _deep_ cloning of variables in JavaScript.

## Installation

    npm install clone

or

    ender build clone

## Example

```js
var clone = require('clone');

var a, b;

a = { foo: { bar: 'baz' } };  // inital value of a

b = clone(a);                 // clone a -> b
a.foo.bar = 'foo';            // change a

console.log(a);               // show a
console.log(b);               // show b
```

This will print:

~~~ javascript
{ foo: { bar: 'foo' } }
{ foo: { bar: 'baz' } }
~~~

**clone** masters cloning simple objects (even with custom prototype), arrays,
Date objects, and RegExp objects. Everything is cloned recursively, so that you
can clone dates in arrays in objects, for example.

## API

`clone(val, circular)`

  * `val` -- the value that you want to clone, any type allowed
  * `circular` -- boolean

    Call `clone` with `circular` set to `false` if you are certain that `obj`
    contains no circular references. This will give better performance if needed.
    There is no error if `undefined` or `null` is passed as `obj`.

`clone.clonePrototype(obj)`

  * `obj` -- the object that you want to clone

Does a prototype clone as
[described by Oran Looney](http://oranlooney.com/functional-javascript/).

## Circular References

~~~ javascript
var a, b;

a = { hello: 'world' };

a.myself = a;
b = clone(a);

console.log(b);
~~~

This will print:

~~~ javascript
{ hello: "world", myself: [Circular] }
~~~

So, `b.myself` points to `b`, not `a`. Neat!

## Test

    npm test

## Bugs and Issues

If you encounter any bugs or issues, feel free to
[open an issue at github](https://github.com/pvorb/node-clone/issues) or send me
an email to <paul@vorb.de>. I also always like to hear from you, if you’re using
my code.

## License

Copyright © 2011-2012 Paul Vorbach

Permission is hereby granted, free of charge, to any person obtaining a copy of
this software and associated documentation files (the “Software”), to deal in
the Software without restriction, including without limitation the rights to
use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of
the Software, and to permit persons to whom the Software is furnished to do so,
subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED “AS IS”, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS
FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR
COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER
IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, OUT OF OR IN CONNECTION WITH THE
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
