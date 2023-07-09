## Quiz Project & Quiz Project Functions

## Example 1 about Function
```javascript

function add3(x, y, z) { 
  console.log("the parameters x, y, z");
  console.log("received", x, y, z);
  return x + y + z;
}
/ 
```
## Example 2 Arrow Function 
```javascript
const add = (x, y) => x + y; 
```
## Example 3 Scope
```javascript
let planet = "Jupiter";
function scope() {
  let planet = "Mars";
  console.log("Inner scope planet:", planet);
}
scope(); // output: Mars
console.log("Outer scope planet:", planet);// output: Jupiter
```

### EX1 
### [Return a Value from a Function with Return](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/return-a-value-from-a-function-with-return)

```javascript
function timesTen(num) {
  return num * 10;
}

const result = timesTen(7);
console.log(result);
```
### EX2
### [Global Scope and Functions](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/global-scope-and-functions)
```javascript
let myGlobal = 10;

function fun1() {
  oopsGlobal = 5;
}

function fun2() {
  let output = "";
  if (typeof myGlobal !== "undefined") {
    output += "myGlobal: " + myGlobal;
  }
  if (typeof oopsGlobal !== "undefined") {
    output += " oopsGlobal: " + oopsGlobal;
  }
  console.log(output);
}

```

### EX3
### [Local Scope and Functions](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/local-scope-and-functions)
```javascript
function myLocalScope() {
  const myVar = "bar";
  console.log('inside myLocalScope', myVar);
}
myLocalScope();

// This throw a ReferenceError
console.log('outside myLocalScope', myVar);

```

### EX4
### [Global vs. Local Scope in Functions](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/global-vs--local-scope-in-functions)
```javascript
  const outerWear = "T-Shirt";

  function myOutfit() {
    const outerWear = "sweater";
    return outerWear;
  }

  myOutfit();
  console.log(myOutfit(),outerWear)
```
### EX5
### [Stand in Line](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/stand-in-line)
```javascript
function nextInLine(arr, item) {
arr.push(item)
arr.shift()
  
  return item;
  // Only change code above this line
}

// Setup
let testArr = [1, 2, 3, 4, 5];

// Display code
console.log("Before: " + JSON.stringify(testArr));
console.log(nextInLine(testArr, 6));
console.log("After: " + JSON.stringify(testArr));
```
