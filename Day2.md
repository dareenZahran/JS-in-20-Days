# Day 2: Expressions, Arrays, and Objects

## Lesson Summary

Welcome to Day 2 of your JavaScript learning journey! In this lesson, we will explore expressions, arrays, and objects in JavaScript. These concepts are fundamental to understanding how to work with values, store data, and create complex data structures. By the end of this lesson, you will have a solid understanding of expressions, arrays, and objects, and how to manipulate them effectively.

### Lesson 1: Expressions

Expressions play a crucial role in JavaScript. Here are the key points covered in this lesson:

- An expression is a combination of literals, variables, and operators that evaluates to a single value.
- Variables allow us to store and remember values. In JavaScript, we declare variables using the `let` and `const` keywords.
- The `let` keyword is used for variables that can be reassigned, while the `const` keyword is used for variables that cannot be reassigned.
- JavaScript evaluates expressions based on the order of operations and resolves them to a value.
- It's important to distinguish between expressions and statements. Expressions produce values, while statements perform actions or control the flow of the program.

### Lesson 2: Arrays

Arrays are essential for storing multiple values in a single variable. Here are the key points covered in this lesson:

- Arrays are ordered collections of items, and each item is stored at an index.
- We can access array items using their index, which starts from 0, and determine the length of an array using the `.length` property.
- Array methods, such as `sort`, `join`, and `concat`, allow us to manipulate arrays in various ways.
- Some array methods mutate the original array, modifying it directly, while others create a new copy without altering the original array.
- It is generally recommended to use immutable data and variables to avoid unintended data mutations and ensure predictable behavior.

### Lesson 3: Objects

Objects are used to represent complex data structures in JavaScript. Here are the key points covered in this lesson:

- Objects store data in key-value pairs, where the key is a string (or symbol) and the value can be of any data type.
- We can access object properties using dot notation (`object.property`) or bracket notation (`object['property']`).
- Objects can have properties that point to functions, known as methods.
- Nested objects and objects within arrays are common in JavaScript to represent hierarchical data structures.
- JavaScript provides predefined objects like `document`, `console`, `Math`, and `String`, which have built-in methods for performing specific operations.
-The(` Object.freeze()`) method can be used to make an object immutable, preventing any modifications to its properties or the addition of new properties.

## Example from course
```javascript
//exercise1
const myName="Dareen";// this canot be change
let compinedAgeOfParents=40+50// we can change it
let board= document.querySelector("#board");
//exercise 2 
let array1=[1,2,3]
let array2=[6,4,5]
array2.sort();//4,5,6
 array1.join("&")//1&2&3
 array1.concat(4)//[1,2,3,4]this dont make a change on the array but it will create new array
 console.log(array1)//[1,2,3]
 array1.push(4)//[1,2,3,4]
 console.log(array1)//[1,2,3,4]

 // the array is mutable we can make change on it 
 const array3=['a','b','c']
 array3[0]='d'//we can do it (the cahnge on the element inside the array)array is mutable
 array3=[1,2]// we canot make this because its const 
 // exercise for object 

 let obj = {name:"dareen",
            age:20 , 
            speake:function(){console.log("my name is dareen")}}

            console.log(obj.name);//dareen
            console.log(obj.speake)//my name is dareen
```
## Exercise
### [Profile Lookup](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/profile-lookup)
```javascript
const contacts = [
    {
      firstName: "Akira",
      lastName: "Laine",
      number: "0543236543",
      likes: ["Pizza", "Coding", "Brownie Points"],
    },
    {
      firstName: "Harry",
      lastName: "Potter",
      number: "0994372684",
      likes: ["Hogwarts", "Magic", "Hagrid"],
    },
    {
      firstName: "Sherlock",
      lastName: "Holmes",
      number: "0487345643",
      likes: ["Intriguing Cases", "Violin"],
    },
    {
      firstName: "Kristian",
      lastName: "Vos",
      number: "unknown",
      likes: ["JavaScript", "Gaming", "Foxes"],
    },
  ];
  
  function lookUpProfile(name, prop) {
    for(let i=0 ; i<=contacts.length;i++){
      if( contacts[i].firstName==name){
          if(contacts[i][prop]!=undefined){
              return contacts[i][prop]
          }
         
      }
     
    }
    return"no such property"
    }
  
  lookUpProfile("Akira", "likes");
```
### [Copy Array Items Using slice()](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-data-structures/copy-array-items-using-slice)
```javascript
function forecast(arr) {
  return arr.slice(2, 4);
}

console.log(forecast(['cold', 'rainy', 'warm', 'sunny', 'cool', 'thunderstorms'])); 
// ['warm', 'sunny']
```
### [Combine Arrays with the Spread Operator](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-data-structures/combine-arrays-with-the-spread-operator)
```javascript
function spreadOut() {
  let fragment = ['to', 'code'];
  let sentence = ['learning',...fragment,'is','fun'];
  return sentence;
}

console.log(spreadOut());
```
