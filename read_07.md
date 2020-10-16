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


# Programming with JavaScript

# Pg 1-24 Intro

### Script - A series of instructions
1. Define the goal
2. Design the script
3. Code each step

### All JavaScript must follow the **Vocabulary** and **Syntax** - Learn it!

### Start with a flowchart before writing any code!

# Expressions + Operators Pgs 74-79

## Expressions Pg 74
* An expresson results in a single value.

* Type 1: Just assigning a value to a variable.
```JavaScript
var color = 'beige';
```

* Type 2: Expressions that use two or more values to return a single value
* You can peform operations on any number of individual values to get a single value
```Javascript
var area = 3 * 2;
```
* The value of area is now 6

## Operators Pg 75
Expressions rely on operators, they allow code to create a single value from multiple values

* **Assignment** operators: assign a value to a variable
* **Arithmetic** operators: perform basic math
* **String** operators: combine two strings: greeting = 'Hi ' + 'Molly';

Covered in Chapter 4
* **Comparison** operators: compare two values and return True or false: buy = 3 > 5; This value is False
* **Logical** operators: combine expressions and return True or False: buy = (5 > 3) && (2 < 4); This value is True

## Arithmetic Operators PG 76
JS contains the following math operators that can be used with numnbers

* Addition | + | Adds one value to another | 10 + 5 | 15 |
* Subtraction | - | Subtracts one value from another | | |
* Divison | / | Divides two values | | |
* Multiply | * | Multiplies | | |
* Increment | ++ | Adds **one** to the current value | i = 10; i++; | 11 |
* Decrement | -- | Subtracts **one** from the current value | i = 10; i--; | 9 |
* Modulus | % | Divides two values and returns the remainder | 10 % 3 | 1 |

Arithmetic order of operations is the same as in algebra

## String Operator Pg 78
There is just one: +
* Joining two strings is called **concatenation**
```javascript
var firstName = 'Nick';
var lastName = 'Magruder';
var fullName = firstName + lastName;
```

If you try to add a number to a string, it just adds it to the string, ie 12Ivy Road.
IF you try to use arithmetic operators on a string, you get **NaN** - not a number

### Using String Operators
```javascript
var greeting = 'Howdy ';
var name = 'Molly';

var welcomeMessage = greeting + name + '!';
```

# Functions 88-94
## What is a Function?
Functions let you group a series of statements together to perform a specific task. If scripts repeat a task, you can reuse the function instead of repeating all the individual steps.

Functions must be named, and when you use that name to run it, its known as **calling** the function

## Declaring a Function
To create a function, name it and then write the statements needed to achieve its task **inside the curly braces**.

```javascript
function sayHello() {
    document.write('Hello!');
}
```
FunctionKeyword FunctionName() {

CodeBlock

}

## Calling a Function
Having declared a function, you can now execute all of the statements it contains by **calling** it

To run, just use the function name followed by (); You can call it as many times as you want in the JS file. Can even be called before it is declared; the browser will find its declaration before it processes the call

```javascript
sayHello();
```
## Declaring Functions that Need Information
If a function needs info to perform its task, when declaring the function you give it **parameters**. In the function, paramters act like **variables**.

* If a function need info to work, you indicate what it needs in the parentheses after the function name.
* Items in the parentheses are known as **parameters** and they act like variable names

```javascript
function getArea(parameterA, parameterB) {
    return parameterA * parameterB;
}
```
## Calling Functions that Need Information
When calling a function with parameters, specify the values for the parentheses. These values are called **arguments**.

Arguments as values
```javascript
getArea(3, 5);
```
Arguments as variables
```javascript
wallWidth = 3;
wallHeight = 5;
getArea(wallWidth, wallHeight);
```

### Parameters VS Arguments
Often used interchangeably but important subtle difference: Parameters become arguments when used as part of the calculation in a function.

## Getting a Single Value out of a function
Some functions return information to the code that called them

This calculateArea() function returns the area to the code that called it

```javascript
function calculateArea(width, height) {
    var area = width * height;
    return area;
}

var wallOne = calculateArea(3,5);
var wallTwo = calculateArea(8,5);
```
