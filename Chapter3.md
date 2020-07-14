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

JavaScript predefines global constants Infinity and NaN to hold the positive infinity and not-a-number value
```javascript
Infinity                  // A positive number too big to represent
Number.POSITIVE_INFINITY  // Same value
1/0                       // => Infinity
Number.MAX_VALUE * 2      // => Infinity; overflow
```

```javascript
-Infinity                 // A negative number too big to represent
Number.NEGATIVE_INFINITY  // The same value
-1/0                      // => -Infinity
-Number.MAX_VALUE * 2     // => -Infinity
```

```javascript
NaN // The not-a-number value
Number.NaN // The same value, written another way
0/0 // => NaN
Infinity/Infinity // => NaN

Number.MIN_VALUE/2 // => 0: underflow
-Number.MIN_VALUE/2 // => -0: negative zero
-1/Infinity // -> -0: also negative 0
-0
```

The following Number properties are defined in ES6
```javascript
Number.parseInt() // Same as the global parseInt() function
Number.parseFloat() // Same as the global parseFloat() function
Number.isNaN(x) // Is x the NaN value?
Number.isFinite(x) // Is x a number and finite?
Number.isInteger(x) // Is x an integer?
Number.isSafeInteger(x) // Is x an integer -(2**53) < x < 2**53?
Number.MIN_SAFE_INTEGER // => -(2**53 - 1)
Number.MAX_SAFE_INTEGER // => 2**53 - 1
Number.EPSILON // => 2**-52: smallest difference between numbers
```
The not-a-number value has one unusual feature in JavaScript: it does not compare equal to any other value, including itself. This means that you can’t write x === NaN to determine whether the value of a variable x is NaN. Instead, you must write x != x or Number.isNaN(x).
```javascript
let zero = 0; // Regular zero
let negz = -0; // Negative zero
zero === negz // => true: zero and negative zero are equal
1/zero === 1/negz // => false: Infinity and -Infinity are not equal
```

### Binary Floating-Point and Rounding Errors
```javascript
let x = .3 - .2;    // thirty cents minus 20 cents
let y = .2 - .1;    // twenty cents minus 10 cents
x === y             // => false: the two values are not the same!
x === .1            // => false: .3-.2 is not equal to .1
y === .1            // => true: .2-.1 is equal to .1
```

Because of rounding error, the difference between the approximations of .3 and .2 is not exactly the same as the difference between the approximations of .2 and .1. It is important to understand that this problem is not specific to JavaScript: it affects any programming language that uses binary floating-point numbers. The computed values are adequate for almost any purpose; the problem only arises when we attempt to compare values for equality.

If these floating-point approximations are problematic for your programs, consider using scaled integers. For example, you might manipulate monetary values as integer cents rather than fractional dollars.

### Arbitrary Precision Integers with BigInt
The type was added to JavaScript mainly to allow the representation of 64-bit integers, which are required for compatibility with many other programming languages and APIs. BigInt literals are written as a string of digits followed by a lowercase letter n.

```javascript
1234n // A not-so-big BigInt literal
0b111111n // A binary BigInt
0o7777n // An octal BigInt
0x8000000000000000n // => 2n**63n: A 64-bit integer
```

You can use BigInt() as a function for converting regular JavaScript numbers or strings to BigInt values:
```javascript
BigInt(Number.MAX_SAFE_INTEGER) // => 9007199254740991n
let string = "1" + "0".repeat(100); // 1 followed by 100 zeros.
BigInt(string) // => 10n**100n: one googol
```

### Dates and Times
JavaScript defines a simple Date class for representing and manipulating the numbers that represent dates and times. JavaScript Dates are objects, but they also have a numeric representation as a timestamp that specifies the number of elapsed milliseconds since January 1, 1970

```javascript
let timestamp = Date.now();   // The current time as a timestamp (a number).
let now = new Date();         // The current time as a Date object.
let ms = now.getTime();       // Convert to a millisecond timestamp.
let iso = now.toISOString();  // Convert to a string in standard format.
```

## Text

The JavaScript type for representing text is the string. A string is an immutable ordered sequence of 16-bit values, each of which typically represents a Unicode character. The length of a string is the number of 16-bit values it contains. JavaScript’s strings (and its arrays) use zero-based indexing: the first 16-bit value is at position 0, the second at position 1, and so on. The empty string is the string of length 0. Java‐ Script does not have a special type that represents a single element of a string. To represent a single 16-bit value, simply use a string that has a length of 1.

In ES6, however, strings are iterable, and if you use the for/of loop or ... operator with a string, it will iterate the actual characters of the string, not the 16-bit values.

### String Literals
To include a string in a JavaScript program, simply enclose the characters of the string within a matched pair of single or double quotes or backticks (' or " or `).

```javascript
"" // The empty string: it has zero characters
'testing'
"3.14"
'name="myform"'
"Wouldn't you prefer O'Reilly's book?"
"τ is the ratio of a circle's circumference to its radius"
`"She said 'hi'", he said.`
```


### Escape Sequences in String Literals

### Working with Strings

### Template Literals

### Pattern Matching
