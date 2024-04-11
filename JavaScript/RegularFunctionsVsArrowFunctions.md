# Functions 
In js there are 2 ways to create functions one : Regular functions and Arrow functions. 
In JavaScript, all functions are objects. They are the instances of the Function type. Because functions are objects, they have properties and methods like other objects.

Functions properties : <br/>
Each function has two important properties: length and prototype.

<li> The <mark style="background-color: #FFF">&nbsp;length&nbsp;</mark> property determines the number of named arguments specified in the function declaration. </li>
<li> The <mark style="background-color: #FFF">&nbsp;prototype&nbsp;</mark> property references the actual function object. </li>

```js
function add(x, y) {
    return x + y;
}

console.log(add.length); // 2
console.log(add.prototype); // Object{}

```

# Regular Functions

```js
function regularFn(a){
    console.log("This is a regular Function");
    return a; // Without this statement undefined will be returned
}

function argsFunc(num1 ,mum2){
    console.log(arguments);
}

argsFunc(1,2);  // Arguments {0: 1, 1: 2}

function duplicateParams(a,b,a){
    console.log(a,b);
}

duplicateParams("a", "b", "c"); // cb

const myObj = {
  a:890,
  arrowFn : (some) => {
    console.log(this);
  },
  regularFn : function(a){
      console.log(this.a);
  }
};

myObj.arrowFn(12); // {}
myObj.regularFn(123); // 890
```
<li> Regular functions are declared using <mark style="background-color: #FFF">&nbsp;function&nbsp;</mark> keyword. A function will always return something, we can explicitly define a return value using return keyword otherwise <mark style="background-color: #FFF"> undefined </mark> is returned </li>

<li> Inside regular functions you have access to <mark style="background-color: #FFF"> &nbsp;arguments&nbsp;</mark> keyword. It's an object that contains all the arguments passed to the function. </li> 

<li> We can use duplicate named parameters, although the duplicate parameter which is defined later will take precedence </li>

<li> Regular functions can be accessed before they are initialzed due to <mark style="background-color: #FFF">&nbsp;function hoisting&nbsp;</mark>. Hoisting in JavaScript is a behaviour where variables and functions are moved to the top of their containing scope during compilation, before the code is executed. 

<li> Regular functions have their own this keyword.  
&nbsp;

# Arrow Functions 

```js
// Different ways of writing a arrow function
let arrowFn = (a) => {
    console.log("This is a arrow function");
    console.log(arguments) // Uncaught ReferenceError: arguments is not defined
    return a;
}

let arrowFn1 = a => a;

let duplicateParams = (a,b,a) => console.log(a,b);

dupliateParams(a,b); // Uncaught Syntax Error : Duplicate named paramter is not allowed 

let thisArrow = () => {
    console.log(this); // Window
}
```

<li> In arrow based functions we don't have to explicitly use return keyword to return some value </li>

<li> There's no arguments object available inside arrow based functions. 

<li> We can not use named duplicate parameters in arrow functions. It will give an syntax based errors. 

<li> Arrow functions are not hoisted to the top level of code and hence if accessed before intialization it will give you error.

<li>Arrow functions, on the other hand, do not have their own this context. Instead, they capture the this value from the surrounding lexical context in which the arrow function was created. In the above code that is <mark style="background-color: #FFF">&nbsp;Window&nbsp;</mark>.  </li> 
