JavaScript Code Conventions
----------------------------

## Formatting

### Line Length

Avoid lines longer than 120 characters.

When a statement will not fit on a single line, it may be necessary to break it. Place the break after an operator, ideally after a comma. A break after an operator decreases the likelihood that a copy-paste error will be masked by semicolon insertion. The next line should be indented 8 spaces.

### Quote

Use single quotes in most situations. Use double quotes when string contains single quote.

```js
var message = 'Today is a huge day!',
    html = "It's my pleasure."
```

### Indentation

JavaScript code should be indented 4 spaces.

## Variables

All variable names begin with a word and use camelCase.

```js
personName
```

 Variables should indicate their type in one of the following ways:

| Type          | Usage              | Example         |
| --------------|--------------------|-----------------|
| HTMLElement   | variable**El**     | bodyEl          |
| jQuery Object | **$**variable      | $body           |
| Array         | variable**s**      | tagIDs          |
| Date          | variable**Time**   | startTime       |
| Boolean       | **is**Variable     | isActive        |
|               | **has**Variable    | hasTag          |
| Event Handler | **handle**Variable | handleLinkClick |
| Object        | variable**Data**   | tagData         |

Currently it has no convention for String and Integer types.

## Constants

Variables or property names that are intended to be constant values (that is, they should not be changed later),
should be in all uppercase with words separate by underscores. Example:

```js
var MAXIMUM_TIMEOUT = 10000;
```

Constants should always be used whenever dealing with:

* `URLs` - These may change in the future, it's best to keep them out of your business logic.
* `Settings` - Things that control the UI or other settings that may change in the future.
* `Repeated strings` - Any string that is used in your code more than once should be a constant.

## Objects

### Properties

Public property names should be formatted in camel case but not in Hungarian notation. This helps to keep the public API clean. For example:

```js
this.className = "My";  //correct
this.strClassName = "My";  //avoid!!
```

Private property names should be formatted in the same way but should be prefixed with an underscore:

```js
var _name = "My";
```

Module properties are considered to be public so using the underscore is not necessary.


### Methods

* Public method names should be formatted in camel case but not in Hungarian notation. For example:

    ```js
    MyClass.prototype.getName = function () { //correct
    };
    MyClass.prototype.fnGetName = function () { //avoid!!
    };
    ```

## Coding Practices

### Abbreviation

Try to avoid any variable or method naming which might cause confusion.

```js
// avoid!
var cont = '...'; // does cont mean content, container, or conter?
var getDef = function () {} // does def mean define, default, or defeat?

// correct
var msg = '...'; // equal to message
var txt = '...'; // equal to text
```

### English Only

You shouldn't write any non-english characters including comments.
For prompting message functions such as `alert()`, you should use `getTrans()` instead of writing non-english words directly.

### Declare Variables at the Beginning of Functions

Whenever possible, all variables used in a function should be declared at the beginning of the function using `var`.

```js
getDimensions = function () {
    var offset = $el.offset(),
        width = $el.outerWidth(),
        height = $el.outerHeight();

    // ,...
};
```

### Create Shortcut Variables for Object Properties

When an object property is referenced two or more times within a function, create a shortcut variable for it.
This reduces the amount of code, enables JavaScript Compressor to perform variable replacement on it,
and reduces the lookup time for the value (each property lookup is more expensive than a property lookup). For example:

```js
// Avoid
$('#foo').on('click', this.handleClick);
$('#foo').addClass('selected');
```

The code above should be rewritten as follows:

```js
// correct
var $foo = $('#foo');
$foo.on('click', this.handleClick);
$foo.addClass('selected');
```

### Avoid Using Globals

Global variables such as **window** and **document** should not be used or assumed to be available.
It's possible that modules may need to work in a locked-down environment where such variables are not accessible.
You should be able to do everything necessary using just facilities provided by modules.

### Condition Operator Usage

The condition operator (*?:*) should be used only to assign variables and never for code that doesn't assign a value.

```js
//proper use
var value = (condition) ? 100 : 200;

//AVOID!!! Doesn't assign a value - use if statement instead
(condition ? doSomething() : null);
```

### Function Declarations

All functions should be declared before they are used.

```js
// avoid!
foo();
function foo() {
    //...
}

// correct
function bar() {
    //...
}
bar();

// correct (anonymous function)
var xyz = function () {
    //...
};
xyz();
```

Anonymous functions should follow the var statement and end with a semi-colon.
This helps make it clear what variables are included in its scope.

There should be no space between the name of a function and the (  (left parenthesis) of its parameter list.
There should be one space between the ) (right parenthesis)  and the { (left curly brace) that begins the statement body.
The body itself is indented four spaces. The }  (right curly brace) is aligned with the line containing the beginning of the declaration of the function.

```js
function getData() {
}

var getData = function () {
};
```

### === and !== Operators.

It is almost always better to use the `===` and `!==` operators. The `\==` and `!=` operators do type coercion.
In particular, do not use `==` to compare against falsy values.

### Statements

All block statements, regardless of the number of lines, should use curly braces. There should be a line break after the left curly brace and the lines inside should be indented. For example:

```js
if (true) { // correct
    doSomething();
}

if (true) doSomething(); // avoid!!

if (true)
    doSomething(); // avoid!!

```

Take *if* Statement as example, the class of statements should have the following form:

```js
if (condition) {
    statements
}

if (condition) {
    statements
} else {
    statements
}

if (condition) {
    statements
} else if (condition) {
    statements
} else {
    statements
}
```

A *for* class of statements should have the following form:

```js
for (initialization; condition; update) {
    statements
}

for (var i = 0, j = items.length; i < j; i++) {
    statements
}

for (var variable in object) {
    if (object.hasOwnProperty(variable)) {
        statements
    }
}
```

### OOP

You should avoid use `this` in OOP JavaScript, it's very confusing because it might means the instance, the window, or the event target.
Always assign to **that** variable at very beginning of a function.

```js
play: function () {
    var that = this;
    ...
}
```

### Naming for Event Handler / Message Listener

The name of a event handler should start with the word **handle**.

```js
_handleClick: function (e) {
    e.preventDefault();
}
```

## Reference

* [Code Conventions for the JavaScript Programming Language](http://javascript.crockford.com/code.html)
* [Google JavaScript style Guide](http://google-styleguide.googlecode.com/svn/trunk/javascriptguide.xml)
* [The Essentials of Writing High Quality JavaScript](http://net.tutsplus.com/tutorials/javascript-ajax/the-essentials-of-writing-high-quality-javascript/)

