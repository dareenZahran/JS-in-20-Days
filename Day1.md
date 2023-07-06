# Day 1: Introduction to JavaScript, DOM, Values & Data Types, and Operators

## Lesson Summary

Welcome to Day 1 of your JavaScript learning journey! Today, we will cover the fundamental concepts of JavaScript, including an introduction to the language, the Document Object Model (DOM), values and data types, and operators. By the end of this lesson, you will have a solid foundation to build upon as you dive deeper into JavaScript.

### Introduction to JavaScript

JavaScript is a versatile programming language widely used in web development. It enables us to add interactivity and dynamic behavior to websites. JavaScript runs on the client-side, meaning it executes directly in the user's web browser. It also has applications beyond the web, such as server-side scripting and creating desktop or mobile applications.

### Document Object Model (DOM)

The Document Object Model, commonly referred to as DOM, is a programming interface for web documents. It represents the structure of HTML documents as a tree-like structure, where each element in the HTML is a node. This tree-like structure allows us to manipulate and interact with web pages dynamically using JavaScript.

With the DOM, we can access and modify elements, change their styles, add or remove HTML content, and handle events like mouse clicks or keyboard input. This gives us the power to create dynamic and interactive web experiences.

### Values & Data Types

In JavaScript, values and data types define the kind of information we can work with. Here are some commonly used data types:

- **Strings**: Used for storing text. They are enclosed in single ('') or double quotes ("").
- **Numbers**: Used for numeric calculations, including whole numbers and decimal values.
- **Booleans**: Represents either `true` or `false` values, used for logical operations and conditional statements.
- **Null**: Represents the intentional absence of any object value.
- **Undefined**: Indicates that a variable has been declared but has not been assigned a value.
- **Objects**: Complex data structures that can hold multiple values and properties.

To work with these data types, we use variables. Variables are named containers that store values. We can declare a variable using the `let`, `const`, or `var` keyword, and assign a value to it using the assignment operator (`=`).

### Operators

Operators in JavaScript are symbols or keywords that perform operations on values and variables. Here are a few important types of operators:

- **Arithmetic Operators**: Used for mathematical calculations, such as addition (`+`), subtraction (`-`), multiplication (`*`), division (`/`), and modulus (`%`).
- **Comparison Operators**: Used to compare values and return a Boolean result, such as equality (`==`, `===`), inequality (`!=`, `!==`), greater than (`>`), less than (`<`), etc.
- **Logical Operators**: Used to combine or invert logical conditions, such as AND (`&&`), OR (`||`), and NOT (`!`).

## Coding Examples from course

```javascript
/*exercise 1
type command in the console to retrive:
1.all the p element
2. the text "x"
3.the number of squares in the board
4. the text "A game you Know"
*/
 
//1.
document.getElementsByTagName("p")
//2. lets say the id is "#id"
document.getElementById("id").textContent
//3.
document.querySelectorAll(".square").length
//4.
document.getElementsByTagName("h2").textContent

/*exercise 2 
1. change the player names to you 
2. swap the player symbols
3. change subtitle to "A game" 
*/

//1. 
document.getElementById("p1-name").textContent="dareen"
//2.
document.getElementById("p1-symbole").textContent="oo"
//3. use append to increment the existing text 
document.querySelector("header h2").append("and Love")

// exercise3 for values & dataType --> type of 
 typeof(true) // boolean
 typeof("true")// String
 typeof(document.title)//String
 typeof("string".length)//number
 typeof(undefined)// undefined
 typeof(null)// object --> but actually its primitiv data type
 typeof(23) // number
 typeof("23")//String

 //exercise 4 
 // append my name 
 document.getElementById("p1-name").append("dareen")
 //get the index of t in title
 document.title.indexOf("T")
 //aske if title have a "javaScript" string or not 
 document.title.includes("javaScript")// fals 
 // to make the header uppercase
document.querySelector("header h1").textContent=document.querySelector("heaser h1").textContent.toUpperCase

// Example 5
let x = 2;
let y = 2;
let addition = x + y;//4
let subtraction = x - y;//0
let multiplication = x * y;//4
let division = x / y; //1
console.log(addition); // 4
console.log(subtraction); // 1
console.log(multiplication); // 4
console.log(division); // 1
```
## Coding Exercises

### [Compound Assignment With Augmented Multiplication](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/compound-assignment-with-augmented-multiplication)
```
#### My Solution
```javascript
let a = 5;
let b = 12;
let c = 4.6;

// Only change code below this line
a *= 5;
b *= 3;
c *= 10;
```

### [Concatenating Strings with the Plus Equals Operator](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/concatenating-strings-with-the-plus-equals-operator)

#### My Solution
```javascript
let myStr ="This is the first sentence. ";
myStr += "This is the second sentence.";
```

### [Use Bracket Notation to Find the Nth-to-Last Character in a String](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/use-bracket-notation-to-find-the-nth-to-last-character-in-a-string)

#### My Solution
```javascript
// Setup
const lastName = "Lovelace";

// Only change code below this line
const secondToLastLetterOfLastName = lastName[lastName.length-2]; // Change this line

```
