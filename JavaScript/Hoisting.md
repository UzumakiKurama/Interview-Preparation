# Hoisting 
Hoisting refers to the process whereby the interpreter appears to move the declaration of functions, variables, classes, or imports to the top of their scope, prior to execution of the code.

+ Being able to use a variable's value in its scope before the line it is declared. <mark style="background-color: #FFF">&nbsp;Value Hoisting&nbsp;</mark>.
+ Being able to reference a variable in its scope before the line it is declared, without throwing a <mark style="background-color: red">&nbsp;ReferenceError&nbsp;</mark>., but the value is always undefined. <mark style="background-color: #FFF">&nbsp;Declarative Hoisting&nbsp;</mark>.
+ Hoisting depends upon how do u declare a value in your code 

Function hoisting is covered [here](./Functions.md); </br>

Some prefer to see let, const, and class as non-hoisting, because the temporal dead zone strictly forbids any use of the variable before its declaration. This dissent is fine, since hoisting is not a universally-agreed term.

    TDZ (Temporal Dead Zone)
    Variables declared using let and const resides in a zone called Temporal Dead Zone. This zone starts when the code execution starts for the block where these variables are defined and ends where they are declared. 

```js
function print() {
    console.log("TDZ") // TDZ starts here for num 
    
    console.log(num);
    let num = 10;// TDZ ends here
}
```

```js
var foo = 1;
function bar() {
    if (!foo) {
        var foo = 10;
	}
    console.log(foo); // 10
}
bar();

// Below and above 2 functions are the same, this is how the code is interpreted
function bar(){
    var foo ;
    if(!foo){
        foo = 10;
    }
    console.log(foo); // 10
}
```