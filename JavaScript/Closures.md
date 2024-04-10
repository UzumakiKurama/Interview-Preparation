# Closures 
Closures are functions inside functions which makes a normal function statefull function. It's a concept that involves the ability of a function to remember and access variables from its outer (enclosing) scope even after the function has finished execution. 

Closures can be used to create self contained modules or self contained state. It also offers abstraction i.e. we can expose what we want to and create objects private to a function.

The JavaScript engine will keep variables around inside functions that have a reference to them, instead of "sweeping" them away after they are popped off the call stack.

```js
function closure(){
    let num ;

    function increment(){num++;}
    function decrement(){num--;}
    function getNum(){console.log(num);}
    
    function init(){
        num = 0;
    }

    init();

    return{
        increment, decrement, getNum
    }
}

let cls = closure(); // closure function is executed
cls.increment(); // but we still have access to num because of closures 
cls.increment();
cls.increment();
cls.getNum(); // 3
cls.decrement();
cls.getNum(); // 2 
```