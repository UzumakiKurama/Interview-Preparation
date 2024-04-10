# Data Types
 + Primitive - Number,String,Null,Undefiend,Symbol,Boolean,BigInt
 + Objects - Array,date etc

 ### Null and Undefined 
 + Null and Undefined are both different things.
 + When a variable is created but not initiliazed, its value at that     time is undefined i.e. absence of definintion. 
 + Null means intentional absence of data 
``` js
    let a ;
    console.log(a) // Undefined

    let str = "";   // This is not null
    let str = null; // This is null
```

 <span style="color : red; font-size:22px"> TypeOf Null returns "object" ?  Why </span> 
    
    The behavior of typeof null returning 'object' in JavaScript is often considered a historical mistake and has been the subject of confusion and discussion in the programming community.

    When JavaScript was first created, the language's designers made a decision to use a specific bit pattern in memory to represent different types of values. Objects were represented with a particular bit pattern that included a "null" value. When checking the type of a value using typeof, JavaScript looks at the bit pattern of the value and returns a corresponding string indicating its type.

    However, when checking the type of null, the bit pattern used for objects was mistakenly identified, leading to the typeof null returning 'object'. This behavior has been retained for compatibility reasons, even though it is technically incorrect.



``` js
    // Numbers
    typeof 3.14 === "number";
    typeof 42 === "number";
    typeof Math.LN2 === "number";
    typeof Infinity === "number";
    typeof NaN === "number"; // Despite being "Not-A-Number"
    typeof Number("1") === "number"; // Number tries to parse things into numbers
    typeof Number("shoe") === "number"; // including values that cannot be type coerced to a number

    typeof 42n === "bigint";

    // Strings
    typeof "" === "string";
    typeof "bla" === "string";
    typeof `template literal` === "string";
    typeof "1" === "string"; // note that a number within a string is still typeof string
    typeof typeof 1 === "string"; // typeof always returns a string
    typeof String(1) === "string"; // String converts anything into a string, safer than toString

    // Booleans
    typeof true === "boolean";
    typeof false === "boolean";
    typeof Boolean(1) === "boolean"; // Boolean() will convert values based on if they're truthy or falsy
    typeof !!1 === "boolean"; // two calls of the ! (logical NOT) operator are equivalent to Boolean()

    // Symbols
    typeof Symbol() === "symbol";
    typeof Symbol("foo") === "symbol";
    typeof Symbol.iterator === "symbol";

    // Undefined
    typeof undefined === "undefined";
    typeof declaredButUndefinedVariable === "undefined";
    typeof undeclaredVariable === "undefined";

    // Objects
    typeof { a: 1 } === "object";

    // use Array.isArray or Object.prototype.toString.call
    // to differentiate regular objects from arrays
    typeof [1, 2, 4] === "object";

    typeof new Date() === "object";
    typeof /regex/ === "object"; // See Regular expressions section for historical results

    // The following are confusing, dangerous, and wasteful. Avoid them.
    typeof new Boolean(true) === "object";
    typeof new Number(1) === "object";
    typeof new String("abc") === "object";

    // Functions
    typeof function() {} === "function";
    typeof class C {} === "function";
    typeof Math.sin === "function";
```