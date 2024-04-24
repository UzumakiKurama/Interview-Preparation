# Synchronous Code
Javascript is synchornous in nature because it is a single threaded language. 
+ Synchronus means code is executed line by line.
+ Each line will wait for the previous line to finish execution.
+ Long running operations block code execution. 

```js
// Example of synchoronus code 

const name = 'Hari';
const greeting = `Hello ${name}`;
console.log(greeting);
```

# Asynchronous Code

+ It is a non-blocking code.
+ 