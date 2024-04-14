# Functions 
In js there are 2 ways to create functions one : Regular functions and Arrow functions. In JavaScript, all functions are objects. They are the instances of the Function type. Because functions are objects, they have properties and methods like other objects.

<mark style="background-color: #FFF">JavaScript functions are first-class citizens. This means that you can store functions in variables, pass them to other functions as arguments, and return them from other functions as values.</mark>

Functions properties : <br/>
Each function has two important properties: length and prototype.
<ul>
<li> The <mark style="background-color: #FFF">&nbsp;length&nbsp;</mark> property determines the number of named arguments specified in the function declaration. </li>
<li> The <mark style="background-color: #FFF">&nbsp;prototype&nbsp;</mark> property references the actual function object. </li> </br>
</ul>
A function type has 3 important methods : <mark style="background-color: #FFF">&nbsp;call()&nbsp;</mark> <mark style="background-color: #FFF">&nbsp;apply()&nbsp;</mark> and <mark style="background-color: #FFF">&nbsp;bind()&nbsp;</mark>
These 3 methods are also known as borrowing functions.

```js
// Example of Call and Apply methods
function emp(name, age){
    this.name = name;
    this.age = age;
    console.log("Name of employee is ", this.name);
    console.log('Age of employee is ', this.age);
}

function setRole(role){
    emp.call(this, 'Abhijeet', 'age');
    this.role = role;
    console.log("Employee Details : ", this);
}

function setDepartment(department){
    emp.apply(this, ['Abhijeet', 'age']);
    this.department = department;
    console.log('Employee Details : ', this);
}

const Engineer = new setRole("Engineer"); 
const Finance = new setDepartment('Finance');

// Example of Bind method
const car = {
    speed : 10,
    start : function(){
        console.log("Start with a speed of : ", this.speed);
    }
}

const plane = {
    speed : 100,
    fly : function(){
        console.log("Fly with a speed of : ", this.speed);
    }
}

const planeStart = car.start.bind(plane);
planeStart();
```

<ul>
<li> Call is a function that helps us replace the value of <mark style="background-color: #FFF">&nbsp;this&nbsp;</mark> inside a function with whatever value we want. </li>

<li> Apply is very similar to call method, where the only difference is that we need to supply arguments as an array[] to apply() method </li>

<li> Bind method creates a new function instance whose this value is bound to the object that we provide. We can execute this new function instance later whenever we need but with call and appy methods the functions are immediately executed.
</ul>

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
<ul>
<li> Regular functions are declared using <mark style="background-color: #FFF">&nbsp;function&nbsp;</mark> keyword. A function will always return something, we can explicitly define a return value using return keyword otherwise <mark style="background-color: #FFF"> undefined </mark> is returned </li>

<li> Inside regular functions you have access to <mark style="background-color: #FFF"> &nbsp;arguments&nbsp;</mark> keyword. It's an object that contains all the arguments passed to the function. </li> 

<li> We can use duplicate named parameters, although the duplicate parameter which is defined later will take precedence </li>

<li> Regular functions can be accessed before they are initialzed due to <mark style="background-color: #FFF">&nbsp;function hoisting&nbsp;</mark>. Hoisting in JavaScript is a behaviour where variables and functions are moved to the top of their containing scope during compilation, before the code is executed. 

<li> Regular functions have their own this keyword. 
</ul>

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
<ul>
<li> In arrow based functions we don't have to explicitly use return keyword to return some value </li>

<li> There's no arguments object available inside arrow based functions. 

<li> We can not use named duplicate parameters in arrow functions. It will give an syntax based errors. 

<li> Arrow functions are not hoisted to the top level of code and hence if accessed before intialization it will give you error.

<li>Arrow functions, on the other hand, do not have their own this context. Instead, they capture the this value from the surrounding lexical context in which the arrow function was created. In the above code that is <mark style="background-color: #FFF">&nbsp;Window&nbsp;</mark>.  </li> 
</ul>