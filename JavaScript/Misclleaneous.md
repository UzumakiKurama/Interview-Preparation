# 9 Things to know about Javascript
1. Javascript is a high level language as developers do not need to concern about memory/resource management like C or C++. JS has a layer of abstraction that takes care of this

2. Auomatic garbage collection in javascript.

3. Javscript is a just-in-time compiled language i.e the entire code is converted into machine code and then it is executed immediately, there is no portable or binary file like in complied languages such as C++ or Java.

4. It is a multi-paradigm lanuage. We can use object oriented programming or procedural programming or Functional programming 

5. Almost everthing in javascript is an object except primitive values such as Numbers, Strings etc. 

6. It is a language with first class functions i.e functions are treated as variables which can be passed as a parameter to another function or can be used as a return value. 

7. Javascript is a dynamic typed language. We don't assign data types to variables when writing JS, instead they are only assigned on run time. 

8. Javascript is a single threaded language which means it has only one call stack that is used to execute the program. Hence it is synchornous in nature. You can write async code when js is run in different enviornments like window or nodejs.

9. Javascript's non-blocking concurrency model is implemented using something called Event Loop. 

# "use strict" 
The purpose of "use strict" is to indicate that the code should be executed in "strict mode". It lets write secure and safe javascript. For ex, it will throw error if we try to use undeclared variables;

Deleting a variable (or object) and a function is not allowed. 
```js
function helloWorld(){
    str = "hello world"
    console.log(str); // This will print hello world without any errors
}
helloWorld()

function helloMars(){
    str = "hello mars"
    console.log(str) // This will give RefferenceError.
}
hellowMars()
```
# Ways to declare objects in Javascripts
There are 4 ways to declare objects in javascript :- 
+ using object literal
+ using Object.create()
+ using constructor (functions) --> constructors are functions that are called using <span style="color : red; ">new</span>
+ using ES6 Classes 

```js 
let employee = {"id" : 1, "name":"Gobind"}; // 1st
employee.address = "Delhi";

let employee2 = Object.create(employee) // 2nd
employee2.name = "Arvind"

function employeeConstructor(){
    this.id = 2;
    this.name = "Ganesh";
}

let employee3 = new employeeConstructor(); //3rd

class Employee{
    constructor(id, name) {
    this.id = id;
    this.name = name;
  }
}

let employee4 = new Employee(1,"Shanko"); // 4th
```

# IIFE (Immediately Invoked Function Expressions)
It is a function that runs as soon as it is defined. This kind of function does not have a name i.e. an anonymous function. 

Use Cases Of IIFE

+ Avoid polluting the global namespace 
+ To create closures
+ Avoid conflict of variable names between libraries and programs.
+ IIFE is used to create private and  public variables and methods
+ It is used to execute the async and await function
+ It is used in JQuery Library
+ It is used to work with require function

# Async and Defer attribute to load scripts

+ Defer : The defer attribute tells the browser not to wait for the script and the broswer will continue to parse the whole HTML. In the background the defer script will keep on downloading and once the DOM is built, then the script gets executed 
    + Scripts with defer never block the page.
    + Scripts with defer always execute when the DOM is ready (but before DOMContentLoaded event).
    + Deferred scripts keep their relative order, just like regular scripts.
```js
<script defer src="https://javascript.info/article/script-async-defer/long.js"></script>
<script defer src="https://javascript.info/article/script-async-defer/small.js"></script>
// Browsers scan the page for scripts and download them in parallel, to improve performance. So in the example above both scripts download in parallel. The small.js probably finishes first.But the defer attribute, besides telling the browser “not to block”, ensures that the relative order is kept. So even though small.js loads first, it still waits and runs after long.js executes.
 ```
 + The async attribute is somewhat like defer. It also makes the script non-blocking. But it has important differences in the behavior.

    + The async attribute means that a script is completely independent:

    + The browser doesn’t block on async scripts (like defer).
    Other scripts don’t wait for async scripts, and async scripts don’t wait for them.


# Currying
It is a technique in functional programming, that transforms the function of multiple arguments into several functions of a single argument in sequence. 

The translation of function happens something like this,

    function simpleFunction(param1, param2, param3, .....) => function 
    curriedFunction(param1)(param2)(param3)(....

```js
function calculateVolume(length) {
    return function (breadth) {
        return function (height) {
            return length * breadth * height;
        }
    }
}
console.log(calculateVolume(4)(5)(6)); //120 

function curry(func){
    function curried(...args){
        if(args.length >= func.length){
            return func(...args);
        }else{
            return function(...more){
                return curried(...args, ...more);
            }
        }
    }
    
    return curried;
}

function mul(a,b,c){
    return a*b*c
}
const multiply = curry(mul);

console.log(multiply(1)(2)(3)); // 6
console.log(multiply(1,2)(3));  // 6
console.log(multiply(1,2,3));   // 6


```
# Event Delegation
Event delegation is a JavaScript programming technique used to efficiently handle events on multiple elements by assigning a single event listener to a common ancestor element. 

```js
<div class="commonParent">
    <li>item1</li>
    <li>item2</li>
    <li>item3</li>
    <li>item4</li>
    <li>item5</li>
    <li>item6</li>
</div>

const commonParent = document.getElementByClassName("commonParent");
commonParent.addEventListener('click', ()=>{
    if(event.target.tagName == "li"){
        console.log(event.target.textContent)
    }
})

// Registering a single event listener on a common ancestral parent.  
```

# Compose and Pipe 
The compose function takes a list of functions as arguments and returns a new function that combines these functions, executing them from right to left. In other words, it applies the rightmost function first and then passes the result to the next function, and so on.

```js
const compose = (...functions) => input => {
  return functions.reduceRight((result, fn) => fn(result), input);
};

// Example usage
const add = x => x + 1;
const square = x => x * x;
const composeAddAndSquare = compose(square, add);

console.log(composeAddAndSquare(3)); // Outputs 16 (3 + 1 = 4, 4 * 4 = 16)
```

The pipe function is similar to compose, but it executes functions from left to right. It takes a list of functions as arguments and returns a new function that applies the leftmost function first and then passes the result to the next function, and so on.

```js
const pipe = (...functions) => input => {
  return functions.reduce((result, fn) => fn(result), input);
};

// Example usage
const add = x => x + 1;
const square = x => x * x;
const pipeAddAndSquare = pipe(add, square);

console.log(pipeAddAndSquare(3)); // Outputs 16 (3 + 1 = 4, 4 * 4 = 16)

```
# Debouncing 
Debouncing is a JavaScript technique used to control the rate at which a function is called. It's particularly useful for scenarios where a function is triggered repeatedly (such as during user input), and you want to ensure that it only gets executed after a certain delay or when the user has stopped inputting for a specified time.

```js
const input = document.getElementById("input");
const textContainer = document.getElementById("textContainer");

const debounce = (fn, delay=1000) => {
    let timeoutId; 

    return function(...args){
        clearTimeout(timeoutId)
        timeoutId = setTimeout(()=>{
            fn(...args);
        }, 1000)
    }
}

const debouncedFunction = debounce((text)=>{
    textContainer.textContent = text;
})

input.addEventListener('input', (e)=>{
    debouncedFunction(e.target.value);
})
```

## Throttle

Throttling is a technique used in JavaScript to limit the frequency at which a function can be called within a specific time period. It ensures that a function is executed at a consistent rate, regardless of how often it's invoked
```js
function throttle(cb, delay) {
  let wait = false;
  let lastArgs = null;

  function waiting(){
    if(lastArgs == null){
        wait = true;
    }else{
        cb(lastArgs); // This is to call the function with the last 
        lastArgs = null;
        setTimeout(waiting, delay)
    }
  }

  return (...args) => {
    if (wait) {
        lastArgs = args;
        return;
    }

    cb(...args);
    wait = true;
    setTimeout(waiting, delay);
  }
}
```
