#JavaScript Methods#

##Basics##


####Values####
There are six basic types of values in JavaScript:

1) numbers - numbers. Special numbers include Infinity and -Infinity and NaN = "Not a number"
2) strings - enclosed between "quotes"
3) Booleans - true or false
4) objects -
5) functions
6) undefined values.

####Operators####
#####Unary Operator#####
Takes in one value:

| Operator | Function | Example |
|----------|----------|---------|
| typeof | produces a string value naming the type of the value you give it | `console.log(typeof 4.5) // -> number` |

#####Binary Operator#####
Takes in two values:

|Operator | Function |
|---------|----------|
|+| adds two numbers or concatenates two strings |
|/| divides two numbers|
|*| multiplies two numbers|
|-| subtracts two numbers|
|%| finds remainder of two numbers when the first is divided by the second|

#####Boolean#####
Summary: "true or false"

[Comparison Operators](http://www.w3schools.com/js/js_comparisons.asp)

1. Greater than or less than or equal to
2. Strings can be compared: uppercase letters are always less than lowercase letters. Based on the [Unicode Standard](http://unicode.org/standard/standard.html) which assigns a number to every character you'll ever need.
3. Only value not equal to itself is NaN



SYNTAX
statements separated by semicolon
variable declaration

Values, Operators, Expressions, Keywords and Comments

Values:
literals
  Numbers ( written with or without decimals)
  Strings (text, written with double or single quotes)
  Expressions (represent fixed values)
variables
  var keyword to define variables
  equal sign used to assign values to variables
Operators
  assignment operator (=) to assign values to variables
  arithmetic operators ( + - * /) to compute values
Keywords
  keywords used to identify actions to be performed
  var keyword tells the brownser to create a new variable

|Keyword | Description | Example|
|--------|-------------|--------|
|break   | Terminates a switch or a loop| ` code ` |
|
|
|

Comments
  Statements that are not executed:
  Code written after a // (for a single line) or between /* and */ are treated as a comment, and will not be executed
Case Sensitive
  camelCasing requires that it does not start with an uppercase letter and lastName is different from lastname
  VAR or Var does not get interptreted as the keyword var
Character Set
  JavaScript uses the Unicode character set
  Unicode covers (almost) all the characters, punctuations and symbols
  http://www.w3schools.com/charsets/ref_html_utf8.asp
  The first 128 characters of Unicode (which correspond one-to-one with ASCII) are encoded using a single octet with the same binary value as ASCII, making valid ASCII text valid UTF-8-encoded Unicode as well.



Popup Boxes
window.alert("some text");
window.confirm("some text");
window.prompt("some text", "defaultText");

document.write()
innerHTML
console.log()


LOOPS
