# Prototype 
Every Object in javascript has a built-in-property called prototype. The prototype is itself an object so it has its own prototype object and the chain goes on and on untill when we reach a prototype that has null for its prototype. This is called as <span style="color: red; font-size:16px"> prototype chaining </span>

<span style="font-style: italic"> Note: The property of an object that points to its prototype is not called prototype. Its name is not standard, but in practice all browsers use "\__proto__". The standard way to access an object's prototype is the Object.getPrototypeOf() method. </span>

When we try to access a property of an object, it will first try to find inside the object if the property is not there then it will search inside the prototype object and it will keep doing so untill it finds null as prototype 

    __proto__ is a historical getter/setter for Prototype
    .__proto__ is not same as Prototype

```js
const Emp = {
    name : "Abhijeet",
    age : 67,
    //We can set the prototype of an object using __proto__ 
    __proto__: {
        position : "Software Engineer"
    }
}

console.log(Object.getPrototypeOf(Emp)); // {position : "Software Engineer"}
console.log(Emp.position); 
// Since Emp does not own a property called position, hence its prototype is searched and then it prints "Software Engineer" 

function Employee(name, age){
    this.name = name;
    this.age = age;
}

// To set the prototype for a function we can use the below method 
Employee.prototype.setPosition = function(position){
    this.position = position;
}

Employee.setPosition(23);
console.log(Employee.position); // 23

const o = { a: 1 };
// The newly created object o has Object.prototype as its [[Prototype]]
// Object.prototype has null as its prototype.
// o ---> Object.prototype ---> null

const b = ["yo", "whadup", "?"];
// Arrays inherit from Array.prototype
// (which has methods indexOf, forEach, etc.)
// The prototype chain looks like:
// b ---> Array.prototype ---> Object.prototype ---> null

function f() {
  return 2;
}
// Functions inherit from Function.prototype
// (which has methods call, bind, etc.)
// f ---> Function.prototype ---> Object.prototype ---> null

const p = { b: 2, __proto__: o };
// It is possible to point the newly created object's [[Prototype]] to
// another object via the __proto__ literal property. (Not to be confused
// with Object.prototype.__proto__ accessors)
// p ---> o ---> Object.prototype ---> null

```

## Implicit constructors of literals
Some literal syntaxes in JavaScript create instances that implicitly set the prototype object. For ex : 

```js
const obj = {
    a : 1,
    b : 2
}
console.log(Object.getPrototypeOf(obj) === Object.prototype) // true
console.log(Object.prototype) // [Object: null prototype] {}
```
Some built-in constructors prototype property are instances themselves. For ex Array.prototype is an empty array, Number.prototype is 0 
```js
console.log(Array.prototype) // [] Empty Array 
console.log(Number.prototype + 1) // 1
```

## Prototype in Functions
All functions have a special property named protoype, well not exactly true. Functions defined using function keyword do have a default property called prototype while the same can not be said for arrow functions. 
```js
function normalFunction(){};
console.log(normalFunction.prototype);
// {
//   constructor: ƒ normalFunction(),
//   [[Prototype]]: {
//     constructor: ƒ Object(),
//     hasOwnProperty: ƒ hasOwnProperty(),
//     isPrototypeOf: ƒ isPrototypeOf(),
//     propertyIsEnumerable: ƒ propertyIsEnumerable(),
//     toLocaleString: ƒ toLocaleString(),
//     toString: ƒ toString(),
//     valueOf: ƒ valueOf()
//   }
// }

const arrowFunction = () => {}
consoel.log(arrowFunction.prototype) // undefined
```
We can create instances of these functions using new operator, which is generally used to implement 
[Prototypal inheritance](Inheritance.md)

Let's try entering some more code into the console:
```js
function doSomething() {}
doSomething.prototype.foo = "bar";
const doSomeInstancing = new doSomething();
doSomeInstancing.prop = "some value";
console.log("doSomeInstancing.prop:     ", doSomeInstancing.prop);
console.log("doSomeInstancing.foo:      ", doSomeInstancing.foo);
console.log("doSomething.prop:          ", doSomething.prop);
console.log("doSomething.foo:           ", doSomething.foo);
console.log("doSomething.prototype.prop:", doSomething.prototype.prop);
console.log("doSomething.prototype.foo: ", doSomething.prototype.foo);
```

    doSomeInstancing.prop:      some value
    doSomeInstancing.foo:       bar
    doSomething.prop:           undefined
    doSomething.foo:            undefined
    doSomething.prototype.prop: undefined
    doSomething.prototype.foo:  bar

