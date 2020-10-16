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


# Operators and Loops

## Comparison Operators: Evaluating Conditions
You can evaluate a stuation by comparing one value in the script to what you expect it might be. The result will be a Boolean: true or false.

### ==
**IS EQUAL TO**
* This operator compares two values  to see if they are the same
* 'Hello' == 'Goodbye' returns False
* 'Hello' == 'Hello' returns True

It is usually preferable to use the strict method:
### ===
**STRICT EQUAL TO**
* Compares two values to cehck that tboth the data type and value are the same.
* '3' === 3 returns false

### !=
**IS NOT EQUAL TO**
* Compares two values to see if they are *not* the same
* 'hello' != 'Goodbye' returns true

It is usually preferable to use the strict method:
### !==
**STRICT NOT EQUAL TO**
* Compares two values to check that both the data type AND value are not the same
* '3' !== 3 returns TRUE
* '3' !== '3' returns FALSE because they ARE the same data type and value

### >
**GREATER THAN**

### <
**LESS THAN**

### >=
**GREATER THAN OR EQUAL TO**

### <=
**LESS THAN OR EQUAL TO**

## Logical Operators Pg 156
Comparison operators return single TRUE/FALSE values while Logical Operators allow you to compare the reults more than one comparison operator

Logical operator below is &&

```javascript
((5 < 2) && (2 >= 3))
```

## &&
**LOGICAL AND**
* Tests more than one condition
* ((2 < 5) && (3 >= 2))
* Returns TRUE
* If both expressions evaluate to true, then the expression returns true. If just one of these returns false, then the expression will return false.

## ||
**LOGICAL OR**
* Tests at least one condition
* ((2 < 5) || (2 < 1))
* Returns TRUE
* If EITHER expression returns returns, only returns false if both are false.

## !
**LOGICAL NOT**
* Takes a single boolean and INVERTS it
* !(2 < 1)
* Returns TRUE
* Reverses the state of an expression.

## Short Circuit Evaluation
If the logic can be figured out in the first expression, there's no need to evaluate the second

## Loops Pg 170
Loops check a condition, if TRUE, it runs a code block again and again until it returns FALSE.

### FOR
To run code a specific number of times, the most common loop. The condition is usually a counter; how many times to run.

### WHILE
The code will continue to loop as long as the condition is TRUE. (Can create an infinite loop)

```javascript
for (var i = 0: i < 10; i++) {
    document.write(i);
}
```
This is a FOR loop that counts to ten. Result would write 0123456789 to the page.

## Loop Counters
A FOR loop uses a counter as a condition, to run the code a specific number of times. It is made up of 3 statements:

### INITIALIZATION
* Create a variable and set it to 0, commonly called i which acts as the counter
* **var i = 0;**
* Variable is created only the first time the loop is run (variable is sometimes called index)
* Sometimes the variable is declared BEFORE the condition:
* var i;
* for (i = 0; i < 10; i++) {
* //code goes here
* }

### CONDITION
* Loop should continue to run until counter reaches a number
* **i < 10;**
* i was iniially set to 0, so now loop will run 10 times
* Condition could also use a variable that contains a number, often called **rounds**:
* var rounds = 3;
* i < (rounds);

### UPDATE
* Every time the loop has run the statements in the curly braces, it adds one to the counter:
* **i++**
* One is added using the increment operator ++
* It is also possible for loops to count downwards using --

## While Loops - Pg 176 - Needs Review




