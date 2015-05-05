## Table of contents

[Files and directories structure](#files-and-directories-structure)
- [Third-party js plugins/libraries](#third-party-js-pluginslibraries)
- [PHP files](#php-files)
- [Javascript files](#javascript-files)

[PHP Standards](#php-standards)
- [Single and Double Quotes](#single-and-double-quotes)
- [Indentation](#indentation)
- [Brace Style](#brace-style)
- [Space Usage](#space-usage)
- [No Shorthand PHP Tags](#no-shorthand-php-tags)
- [Remove Trailing Spaces](#remove-trailing-spaces)
- [Naming Conventions](#naming-conventions)

[Javascript standards](#javascript-standards)
- [Variable declaration](#variable-declaration)
- [Objects](#objects)
- [Array and Object literals](#array-and-object-literals)
- [Modifying prototypes of builtin objects](#modifying-prototypes-of-builtin-objects)
- [Standards features](#standards-features)
- [Spacing](#spacing)
- [Braces](#braces)
- [Indenting wrapped lines](#indenting-wrapped-lines)
- [Blank lines](#blank-lines)
- [Binary and Ternary Operators](#binary-and-ternary-operators)
- [Strings](#strings)
- [Semicolons](#semicolons)
- [Constants](#constants)
- [Nested functions](#nested-functions)
- [Method and property definitions](#method-and-property-definitions)
- [Closures](#closures)
- [Naming Conventions](#naming-conventions-1)
- [“Yoda” Conditions](#yoda-conditions)
- [Iteration](#iteration)
- [Comments](#comments)
- [Bad practice](#bad-practice)

[LESS/CSS Standarts](#lesscss-standarts)
## Files and directories structure

- All php code files should be placed in **include** directory.
- All templates should be placed in **include/template** directory.
- All js files should be placed in **assets/js** directory.
- All less files should be placed in assets/less
- **Important:** css files shouldn't be modified directly, please modify less and then compile it to css.

### Third-party js plugins/libraries
All Third party plugins should be added as git submodule if it is possible(repo exists) in assets/lib. Libs shouldn't be modified and if it is required to add some changes use javascript prototyping pattern inside vendor's lib.

### PHP files

Files should be named descriptively using lowercase letters. Hyphens should separate words.
> my-plugin-name.php

Class file names should be based on the class name with class- prepended and the underscores in the class name replaced with hyphens, for example WP_Error becomes:
> class-wp-error.php

PHP/Html template file name should have **tpl.php** extension:
> navbar.tpl.php

### Javascript files


## PHP Standards
Coding standards basically taken from WordPress coding standards. Visit [this link](http://make.wordpress.org/core/handbook/coding-standards/php/) for more details.

### Single and Double Quotes
Use single and double quotes when appropriate. If you’re not evaluating anything in the string, use single quotes.
Text that goes into attributes should be run through esc_attr() so that single or double quotes do not end the attribute value and invalidate the HTML and cause a security issue. See Data Validation in the Codex for further details.

### Indentation
Use real tabs and not spaces.
For associative arrays, values should start on a new line. Note the comma after the last array item: this is recommended because it makes it easier to change the order of the array, and makes for cleaner diffs when new items are added.
```php
$my_array = array(
[tab]'foo'   => 'somevalue',
[tab]'foo2'  => 'somevalue2',
[tab]'foo3'  => 'somevalue3',
[tab]'foo34' => 'somevalue3',
);
```
### Brace Style
```php
if ( condition ) {
    action1();
    action2();
} elseif ( condition2 && condition3 ) {
    action3();
    action4();
} else {
    defaultaction();
}
```
if you have a really long block, consider whether it can be broken into two or more shorter blocks or functions. If you consider such a long block unavoidable, please put a short comment at the end so people can tell at glance what that ending brace ends – typically this is appropriate for a logic block, longer than about 35 rows, but any code that’s not intuitively obvious can be commented.

Braces should always be used, even when they are not required.
```
if ( condition ) {
    action0();
}
```
### Space Usage
Always put spaces after commas, and on both sides of logical, comparison, string and assignment operators.
```php
x == 23
foo && bar
! foo
array( 1, 2, 3 )
$baz . '-5'
$term .= 'X'
```
Put spaces on both sides of the opening and closing parenthesis of if, elseif, foreach, for, and switch blocks.

```php
foreach ( $foo as $bar ) { ...
```
When defining a function, do it like so:
```php
function my_function( $param1 = 'foo', $param2 = 'bar' ) { ...
```
When calling a function, do it like so:
```php
my_function( $param1, func_param( $param2 ) );
```
When performing logical comparisons, do it like so:
```php
if ( ! $foo ) { ...
```
When type casting, do it like so:
```php
foreach ( (array) $foo as $bar ) { ...
 
$foo = (boolean) $bar;
```
When referring to array items, only include a space around the index if it is a variable, for example:
```php
$x = $foo['bar']; // correct
$x = $foo[ 'bar' ]; // incorrect
 
$x = $foo[0]; // correct
$x = $foo[ 0 ]; // incorrect
 
$x = $foo[ $bar ]; // correct
$x = $foo[$bar]; // incorrect
```

### No Shorthand PHP Tags
**Important**: Never use shorthand PHP start tags. Always use full PHP tags.
```php
<?php ... ?>
<?php echo $var; ?>
```
### Remove Trailing Spaces
Remove trailing whitespace at the end of each line of code. Omitting the closing PHP tag at the end of a file is preferred. If you use the tag, make sure you remove trailing whitespace.

### Naming Conventions
Use lowercase letters in variable, action, and function names (never camelCase). Separate words via underscores. 

Class names should use capitalized words separated by underscores. Any acronyms should be all upper case.
```php
class Walker_Category extends Walker { [...] }
class WP_HTTP { [...] }
```
Constants should be in all upper-case with underscores separating words:

## Javascript standards
Coding standards basically taken from [Wordpress coding standards](http://make.wordpress.org/core/handbook/coding-standards/javascript/) and [Google JavaScript Style Guide](https://google-styleguide.googlecode.com/svn/trunk/javascriptguide.xml).

Check also [this link](https://github.com/stevekwan/best-practices/blob/master/javascript/best-practices.md) for the best practice in coding

### Variable declaration
Each function should begin with a single comma-delimited var statement that declares any local variables necessary. If a function does not declare a variable using var, that variable can leak into an outer scope (which is frequently the global scope, a worst-case scenario), and can unwittingly refer to and modify that data.

Assignments within the var statement should be listed on individual lines, while declarations can be grouped on a single line. Any additional lines should be indented with an additional tab. Objects and functions that occupy more than a handful of lines should be assigned outside of the var statement, to avoid over-indentation.
```javascript
// Good
var k, m, length,
    // Indent subsequent lines by one tab
    value = 'WordPress';
 
// Bad
var foo = true;
var bar = false;
var a;
var b;
var c;
```
### Objects
Object declarations can be made on a single line if they are short (remember the line length guidelines). When an object declaration is too long to fit on one line, there must be one property per line. Property names only need to be quoted if they are reserved words or contain special characters:

```javascript
// Preferred
var map = {
    ready: 9,
    when: 4,
    'you are': 15
};
 
// Acceptable for small objects
var map = { ready: 9, when: 4, 'you are': 15 };
 
// Bad
var map = { ready: 9,
    when: 4, 'you are': 15 };
```
### Array and Object literals
Use Array and Object literals instead of Array and Object constructors. Array constructors are error-prone due to their arguments. Because of this, if someone changes the code to pass 1 argument instead of 2 arguments, the array might not have the expected length.

To avoid these kinds of weird cases, always use the more readable array literal.
```javascript
// Bad
// Length is 3.
var a1 = new Array(x1, x2, x3);

// Length is 2.
var a2 = new Array(x1, x2);

// If x1 is a number and it is a natural number the length will be x1.
// If x1 is a number but not a natural number this will throw an exception.
// Otherwise the array will have one element with x1 as its value.
var a3 = new Array(x1);

// Length is 0.
var a4 = new Array();

// Good
var a = [x1, x2, x3];
var a2 = [x1, x2];
var a3 = [x1];
var a4 = [];
```
Object constructors don't have the same problems, but for readability and consistency object literals should be used.
```javascript
// Bad
var o = new Object();

var o2 = new Object();
o2.a = 0;
o2.b = 1;
o2.c = 2;
o2['strange key'] = 3;

// Good
var o = {};

var o2 = {
  a: 0,
  b: 1,
  c: 2,
  'strange key': 3
};
```

### Modifying prototypes of builtin objects
Modifying builtins like Object.prototype and Array.prototype are strictly forbidden. Modifying other builtins like Function.prototype is less dangerous but still leads to hard to debug issues in production and should be avoided.

### Standards features
For maximum portability and compatibility, always prefer standards features over non-standards features (e.g., string.charAt(3) over string[3] and element access with DOM functions instead of using an application-specific shorthand).

### Spacing
Use spaces liberally throughout your code. “When in doubt, space it out.”

These rules encourage liberal spacing for improved developer readability. The minification process creates a file that is optimized for browsers to read and process.

- Indentation with **tabs**.
- No whitespace at the end of line or on blank lines.
- Lines should usually be no longer than 80 characters, and should not exceed 100. This is a “soft” rule, but long lines generally indicate unreadable or disorganized code.
- if/else/for/while/try blocks should always use braces, and always go on multiple lines.
- Unary special-character operators (e.g., ++, --) must not have space next to their operand.
- Any , and ; must not have preceding space.
- Any ; used as a statement terminator must be at the end of the line.
- Any : after a property name in an object definition must not have preceding space.
- The ? and : in a ternary conditional must have space on both sides.
- No filler spaces in empty constructs (e.g., {}, [], fn()).
- There should be a new line at the end of each file.
- Any ! negation operator must not have a following space.
- All function bodies are indented by 2 spaces, even if the entire file is wrapped in a closure.

### Braces
Because of implicit semicolon insertion, always start your curly braces on the same line as whatever they're opening. For example:

```javascript
if (something) {
  // ...
} else {
  // ...
}
```

### Indenting wrapped lines
Except for array literals, object literals, and anonymous functions, all wrapped lines should be indented either left-aligned to a sibling expression above, or four spaces (not two spaces) deeper than a parent expression (where "sibling" and "parent" refer to parenthesis nesting level).
```javascript
someWonderfulHtml = '' +
                    getEvenMoreHtml(someReallyInterestingValues, moreValues,
                                    evenMoreParams, 'a duck', true, 72,
                                    slightlyMoreMonkeys(0xfff)) +
                    '';

thisIsAVeryLongVariableName =
    hereIsAnEvenLongerOtherFunctionNameThatWillNotFitOnPrevLine();

thisIsAVeryLongVariableName = siblingOne + siblingTwo + siblingThree +
    siblingFour + siblingFive + siblingSix + siblingSeven +
    moreSiblingExpressions + allAtTheSameIndentationLevel;

thisIsAVeryLongVariableName = operandOne + operandTwo + operandThree +
    operandFour + operandFive * (
        aNestedChildExpression + shouldBeIndentedMore);

someValue = this.foo(
    shortArg,
    'Some really long string arg - this is a pretty common case, actually.',
    shorty2,
    this.bar());

if (searchableCollection(allYourStuff).contains(theStuffYouWant) &&
    !ambientNotification.isActive() && (client.isAmbientSupported() ||
                                        client.alwaysTryAmbientAnyways())) {
  ambientNotification.activate();
}
```
### Blank lines
Use newlines to group logically related pieces of code. For example:
```javascript
doSomethingTo(x);
doSomethingElseTo(x);
andThen(x);

nowDoSomethingWith(y);

andNowWith(z);
```
### Binary and Ternary Operators
Always put the operator on the preceding line. Otherwise, line breaks and indentation follow the same rules as in other Google style guides. This operator placement was initially agreed upon out of concerns about automatic semicolon insertion. In fact, semicolon insertion cannot happen before a binary operator, but new code should stick to this style for consistency.
```javascript
var x = a ? b : c;  // All on one line if it will fit.

// Indentation +4 is OK.
var y = a ?
    longButSimpleOperandB : longButSimpleOperandC;

// Indenting to the line position of the first operand is also OK.
var z = a ?
        moreComplicatedB :
        moreComplicatedC;
```
This includes the dot operator.
```javascript
var x = foo.bar().
    doSomething().
    doSomethingElse();
```
### Strings
Use single-quotes for string literals:
```javascript
var myStr = 'strings should be contained in single quotes';
When a string contains single quotes, they need to be escaped with a backslash (\):
```
```javascript
// Escape single quotes within strings:
'Note the backslash before the \'single quotes\'';
```
### Semicolons
Use them. Never rely on Automatic Semicolon Insertion (ASI).

### Constants
Use NAMES_LIKE_THIS for constant values and @const to indicate a constant (non-overwritable) pointer (a variable or property).

Never use the const keyword as it's not supported in Internet Explorer.

### Nested functions
Nested functions can be very useful, for example in the creation of continuations and for the task of hiding helper functions. Feel free to use them.

### Method and property definitions
While there are several ways to attach methods and properties to an object created via "new", the preferred style for methods is:
```javascript
Foo.prototype.bar = function() {
  /* ... */
};
```
The preferred style for other properties is to initialize the field in the constructor:
```javascript
/** @constructor */
function Foo() {
  this.bar = value;
}
```
Why?

Current JavaScript engines optimize based on the "shape" of an object, adding a property to an object (including overriding a value set on the prototype) changes the shape and can degrade performance.

### Closures
The ability to create closures is perhaps the most useful and often overlooked feature of JS. Here is a good description of how closures work.

One thing to keep in mind, however, is that a closure keeps a pointer to its enclosing scope. As a result, attaching a closure to a DOM element can create a circular reference and thus, a memory leak. For example, in the following code:
```javascript
function foo(element, a, b) {
  element.onclick = function() { /* uses a and b */ };
}
```
the function closure keeps a reference to element, a, and b even if it never uses element. Since element also keeps a reference to the closure, we have a cycle that won't be cleaned up by garbage collection. In these situations, the code can be structured as follows:
```javascript
function foo(element, a, b) {
  element.onclick = bar(a, b);
}

function bar(a, b) {
  return function() { /* uses a and b */ };
}
```
### Naming Conventions
Variable and function names should be full words, using camel case with a lowercase first letter. Constructors intended for use with new should have a capital first letter (UpperCamelCase). 

Names should be descriptive, but not excessively so. Exceptions are allowed for iterators, such as the use of i to represent the index in a loop.

### “Yoda” Conditions
For consistency with the PHP code standards, whenever you are comparing an object to a string, boolean, integer, or other constant or literal, the variable should always be put on the right hand side, and the constant or literal put on the left.
```javascript
if ( true === myCondition ) {
    // Do stuff
}
```
### Iteration
When iterating over a large collection using a for loop, it is recommended to store the loop’s max value as a variable rather than re-computing the maximum every time:

```javascript
// Good & Efficient
var i, max;
 
// getItemCount() gets called once
for ( i = 0, max = getItemCount(); i < max; i++ ) {
    // Do stuff
}
 
// Bad & Potentially Inefficient:
// getItemCount() gets called every time
for ( i = 0; i < getItemCount(); i++ ) {
    // Do stuff
}
```

“A little bizarre, it is, to read. Get used to it, you will.”
### Comments

Comments come before the code to which they refer, and should always be preceded by a blank line. Capitalize the first letter of the comment, and include a period at the end when writing full sentences. There must be a single space between the comment token (//) and the comment text.

All files, classes, methods and properties should be documented with JSDoc comments with the appropriate tags and types. Textual descriptions for properties, methods, method parameters and method return values should be included unless obvious from the property, method, or parameter name.
```javascript
/**
 * Illustrates line wrapping for long param/return descriptions.
 * @param {string} foo This is a param with a description too long to fit in
 *     one line.
 * @return {number} This returns something that has a description too long to
 *     fit in one line.
 */
project.MyClass.prototype.method = function(foo) {
  return 5;
};
```
Like JavaDoc, JSDoc supports many HTML tags, like <code>, <pre>, <tt>, <strong>, <ul>, <ol>, <li>, <a>, and others.

This means that plaintext formatting is not respected. So, don't rely on whitespace to format JSDoc.
```javascript
/**
 * Computes weight based on three factors:
 * <ul>
 * <li>items sent
 * <li>items received
 * <li>last timestamp
 * </ul>
 */
```
### Bad practice
- Never use with(){}.
- Try to avoid eval().
- No Multiline string literals. The whitespace at the beginning of each line can't be safely stripped at compile time; whitespace after the slash will result in tricky errors; and while most script engines support this, it is not part of ECMAScript. Use string concatenation instead.
- No Internet Explorer's conditional comments.

## LESS/CSS Standards

### Spacing

- Indentation with **4 spaces**.
- No whitespace at the end of line or on blank lines.

## Documentation