---
description: Input numeric Props
---

# InputNumeric

### Default value

The current number box value.

Type: [Number](http://www.w3schools.com/js/js\_numbers.asp)

Default Value: 0

### disabled

Specifies whether the UI component responds to user interaction.

Type: [Boolean](http://www.w3schools.com/js/js\_booleans.asp)

Default Value: false

### format

Specifies the value's display format and controls user input accordingly

```javascript
const number = 1.2345;
 
type: "fixedPoint" // 1
type: "decimal" // 1.2345
type: "percent" // 123%
type: "currency" // $1

const largeNumber = 1000000000;
 
type: "exponential" // 1.0E+9
type: "thousands" // 1,000,000K
type: "millions" // 1,000M
type: "billions" // 1B
type: "trillions" // 0T
type: "largeNumber" // 1B (uses "thousands", "millions", "billions", or "trillions", depending on the value)
```

#### Custom format string

Use Unicode Locale Data Markup Language (LDML) patterns to specify a custom format string. An LDML pattern consists of wildcard characters and characters displayed as is. The **format** property supports the following wildcard characters:

<table><thead><tr><th width="180">Format character</th><th>Description</th></tr></thead><tbody><tr><td>0</td><td>A digit. Displays '0' if the formatted number does not have a digit in that position.</td></tr><tr><td>#</td><td>Up to 15 of leading digits, a single digit, or nothing. If this character goes first in the format string, it can match multiple leading digits (before the decimal point). Subsequent characters match a single digit. If the formatted number does not have a digit in the corresponding position, it displays nothing.<br>For example, if you apply format "#0.#" to "123.45", the result is "123.4".</td></tr><tr><td>.</td><td>A decimal separator.<br>Actual character depends on locale.</td></tr><tr><td>,</td><td>A group separator.<br>Actual character depends on locale.</td></tr><tr><td>%</td><td>The percent sign. Multiplies the input value by 100.</td></tr><tr><td>;</td><td>Separates positive and negative format patterns.<br>For example, the "#0.##;(#0.##)" format displays a positive number according to the pattern before the semicolon (";"), and a negative number according to the pattern after the semicolon (";").<br>If you do not use this character and the additional pattern, negative numbers display a minus ("-") prefix.</td></tr><tr><td>Escape characters</td><td>You can display the special characters above as literals if you enclose them in single quotation marks.<br>For example, '%'.</td></tr><tr><td>Other characters</td><td>You can add any literal characters to the beginning or end of the format string.</td></tr></tbody></table>

The examples below demonstrate the behavior of "#" and "0" in fractional numbers:



```javascript
const number = 1234.567;
 
// Leave the first digit before the decimal point and round up the decimal
format: "0.0" // 4.6
 
const smallNumber = 0.1234;
 
// Display nothing in place of a digit
format: "#.#" // .1
 
const largeNumber = 123456.789;
 
// Add a group separator
format: ",##0.###" // 123,456.789
```

The examples below show different ways to apply percentage formatting to decimals. Use caution if your format string starts with a zero ('0'), because the formatted number may lose leading digits.

```javascript
const smallNumber = 0.01234;
 
// Represent as a percentage and limit to two decimal digits
format: "#0.##%" // 1.23%
 
// Add a percent sign and limit to two decimal digits
format: "#0.##'%'" // 0.01%
```

#### precision

Specifies a precision for values of numeric or currency format types.

Type: [Number](http://www.w3schools.com/js/js\_numbers.asp)

### label

Specifies a text string used to annotate the editor's value.

Type: [String](http://www.w3schools.com/js/js\_strings.asp)

Default Value: 'Input Numeric'

### max

The maximum value accepted by the number box.

Type: [Number](http://www.w3schools.com/js/js\_numbers.asp)

Default Value: undefined

### min

The minimum value accepted by the number box.

Type: [Number](http://www.w3schools.com/js/js\_numbers.asp)

Default Value: undefined

### step

Specifies how much the UI component's value changes when using the spin buttons, Up/Down arrow keys, or mouse wheel.

Type: [Number](http://www.w3schools.com/js/js\_numbers.asp)

Default Value: 1
