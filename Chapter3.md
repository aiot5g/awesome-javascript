# Chapter 3 Types, Values, and Variables
awesome-javascript

## Numbers

JavaScript’s primary numeric type, Number, is used to represent integers and to approximate real numbers.

### Integer Literals
- base-10: a base-10 integer is written as a sequence of digits
- base-16: a hexadecimal (base-16) values, 0x or 0X
- base-2: a binary value, 0b or 0B, available in ES6 or later
- base-8: a octal value, 0o or 0O, available in ES6 or later

A hexadecimal literal begins with 0x or 0X, followed by a string of hexadecimal digits. A hexadecimal digit is one of the digits 0 through 9 or the letters a (or A through f (or F), which represent values 10 through 15.

And if you'd like to use syntax highlighting, include the language:

```javascript
console.log(0xff)
```

### Floating-Point Literals
Floating-point literals can have a decimal point; they use the traditional syntax for real numbers. A real value is represented as the integral part of the number, followed by a decimal point and the fractional part of the number.

Floating-point literals may also be represented using exponential notation: a real number followed by the letter e (or E), followed by an optional plus or minus sign, followed by an integer exponent.

*syntax: [digits][.digits][(E|e)[(+|-)]digits]*

Separators in Numeric Literals: use underscores within numeric literals to break long literals up into chunks that are easier to read

```javascript
let billion = 1_000_000_000;    // Underscore as a thousands separator.
let bytes = 0x89_AB_CD_EF;      // As a bytes separator.
let bits = 0b0001_1101_0111;    // As a nibble separator.
let fraction = 0.123_456_789;   // Works in the fractional part, too.
```

### Arithmetic in JavaScript
The arithmetic operators: + for addition, - for subtraction, * for multiplication, / for division, and % for modulo (remainder after division).

* basic arithmetic operators
* ES6 defines more functions on the Math object

```javascript
Math.pow(2,53)          // => 9007199254740992: 2 to the power 53
Math.round(.6)          // => 1.0: round to the nearest integer
Math.ceil(.6)           // => 1.0: round up to an integer
Math.floor(.6)          // => 0.0: round down to an integer
Math.abs(-5)            // => 5: absolute value
Math.max(x,y,z)         // Return the largest argument
Math.min(x,y,z)         // Return the smallest argument
Math.random()           // Pseudo-random number x where 0 <= x < 1.0
Math.PI                 // π: circumference of a circle / diameter
Math.E                  // e: The base of the natural logarithm
Math.sqrt(3)            // => 3**0.5: the square root of 3
Math.pow(3, 1/3)        // => 3**(1/3): the cube root of 3
Math.sin(0)             // Trigonometry: also Math.cos, Math.atan, etc.
Math.log(10)            // Natural logarithm of 10
Math.log(100)/Math.LN10 // Base 10 logarithm of 100
Math.log(512)/Math.LN2  // Base 2 logarithm of 512
Math.exp(3)             // Math.E cubed
```

```javascript
Math.cbrt(27)       // => 3: cube root
Math.hypot(3, 4)    // => 5: square root of sum of squares of all arguments
Math.log10(100)     // => 2: Base-10 logarithm
Math.log2(1024)     // => 10: Base-2 logarithm
Math.log1p(x)       // Natural log of (1+x); accurate for very small x
Math.expm1(x)       // Math.exp(x)-1; the inverse of Math.log1p()
Math.sign(x)        // -1, 0, or 1 for arguments <, ==, or > 0
Math.imul(2,3)      // => 6: optimized multiplication of 32-bit integers
Math.clz32(0xf)     // => 28: number of leading zero bits in a 32-bit integer
Math.trunc(3.9)     // => 3: convert to an integer by truncating fractional part
Math.fround(x)      // Round to nearest 32-bit float number
Math.sinh(x)        // Hyperbolic sine. Also Math.cosh(), Math.tanh()
Math.asinh(x)       // Hyperbolic arcsine. Also Math.acosh(), Math.atanh()
```

Arithmetic in JavaScript does not raise errors in cases of overflow, underflow, or division by zero.

* Overflow: when the result of a numeric operation is larger than the largest representable number (overflow), the result is a special infinity value, Infinity.
* Underflow: when the result of a numeric operation is closer to zero than the smallest representable number.
* Division by zero is not an error in JavaScript: it simply returns infinity or negative infinity.

There is one exception, however: zero divided by zero does not have a welldefined value, and the result of this operation is the special not-a-number value, NaN.
