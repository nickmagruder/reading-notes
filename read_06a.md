Table of Contents
* [Home](https://nickmagruder.github.io/reading-notes/)
* [Embracing the Growth Mindset](growth_mindset.md)
* [Read 01: Markdown](markdown.md)
* [Read 02: Text Editors and Command Prompt](text_editors.md)
* [Read 03: Revisions and the Cloud](read_03.md)
* [Read: 04 - Structure web pages with HTML](read_04.md)
* [Read: 05 - Design web pages with CSS](read_05.md)
* [Read: 06a - Dynamic web pages with JavaScript](read_06a.md)
* [Read: 06b - Computer Architecture and Logic](read_06b.md)
* [Read: 07 - Programming with JavaScript](read_07.md)
* [Read: 08 - Operators and Loops](read_08.md)
* [Read 04: HTML & Design](read_04.md)

# Dynamic Web Pages with JavaScript

##Statements
A script is a serious of instructions... a **statement** is an individual instruction, statements end with a semicolon

## HTML, CSS and JavaScript
Progressive Enhancement
* HTML - Content Layer
* CSS - Presentation Layer
* JS - Behavior/interactivity layer


## JavaScript is case sensitive

* Write comments to explain what the code does
* /* multi line */
* // Single Line

## Don't use document.write !!!

# Objects & Methods
This line of code is referred to as **calling** a method of an object

```JavaScript
document.write('Good Afternoon!');
```
**Member.memberoperator('parameters')**

### Place scripts in the HTML where you want the script to be written

# Chapter 2 - Pg. 54 - Basic JavaScript Instructions

## Statements
* Each individual instruction or step is a **statement**, and should end with a **;**
* Curly braces indicate the start and end of a code block
* JS is case sensitive
* Statements are instructions, each starts on a new line and end with a semicolon, telling the browser when the step is over
* Some statements are surrounded in curly braces, these are known as **code blocks**. The closing curly brace is **not** followed by a semicolon

### Comments
* Just like in HTML or CSS, insert comments to explain what a statement or code block is accomplishing

```JavaScript
/* Multi
line
comment */ 
```

```JavaScript
//inline comment 
```

## Variables
* Scripts must temporarily store bits of info they need to do their jobs, this is stored in **variables**
* Variables are comparable to short-term memory
* Well-named because the data stored in a variable can change each time a script runs

### How to declare Variables
* Variables must be "declared", or named

```JavaScript
var quantity; 
```

VariableKeyword  VariableName;

* if the variable name is more than one word, write in camelCase

### Assigning value to variables
* Once a variable is created(named) you can **assign a value** to the variable

```JavaScript 
quantity = 3; 
```

VariableName AssignmentOperator VariableValue;

* The = is an assignment operator, it says that you are going to assign a value to the variable, it is also used to **update** the value
* Until a value has been assigned, the value is **undefined**.

## Data Types - Pg 62
* JS distinguishes between numbers, strings and booleans(true/false)

* Numeric data type: Numbers - 999999.99
* String Data type: 'This is a string' - can contain HTML markup
* Boolean: True or False, light a light switch

### Using a Variable to Store a Number
* Once a value is applied to a variable, use the variable name to represent that value

### Using a Variable to Store a String
* Within quotes, must be written on one line 

```JavaScript
var userName;
    userName = 'Nick';
```

### Using quotes inside a string
* If you need to use a " or ' inside a string, use the opposite " or ' to enclose that string
* You can also "escape" the quote mark with a backslash, ie \"

### Using a variable to store a Boolean

```JavaScript
var inStock;
    inStock = 'False';
```

### Shorthand for creating variables
```JavaScript
var price = 5;
var quantity = 14;
var total = price * quantity
```

OR

```JavaScript
var price, quantity, total;
price = 5;
quantity = 14;
total = price * quantity;
```

OR
```JavaScript
var price = 5, quantity = 14;
var total = price * quantity;
```

## Changing the Value of a Variable
* Just right the variable and = theNewValue;
* inStock = false;

## Rules for Naming Variables
1. Name must begin with a letter, $, or _. It must NOT start with a number
2. Name can contain letters, numers, $ or _. Do NOT use a - or . in a variable name.
3. Do NOT use keywords or reserved words, for example var.
4. names are case sensitive
5. Use a name that describes the type of info the variable contains, ie: firstName or quantity
6. Use camelCase










