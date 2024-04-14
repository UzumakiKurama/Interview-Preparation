# Promise
<ul>
<li> A promise is an object that encapsulates the result of an asynchronous operation.
<li>A promise starts in the pending state and ends in either a fulfilled state or a rejected state.
<li>Use then() method to schedule a callback to be executed when the promise is fulfilled, and catch() method to schedule a callback to be invoked when the promise is rejected.
<li>Place the code that you want to execute in the finally() method whether the promise is fulfilled or rejected.
</ul>

```js
const myPromise = new Promise(function(resolve,reject){
    if(Math.random() >= 0.5){
        resolve("Promise is resolved");
    }else{
        reject("Promise failed");
    }
})

myPromise.then(res=> console.log(res)).catch(error => console.log(error))
```

## Promise.all() 

The promise.all() method accepts an array of promises as input and returns a single promise when all the input promises have been resolved. The return promise resolves to an array of results of the input promises. 

<mark style="background-color: #FFF"> If any of the promises are rejected then, Promise.all() method will give a rejected promise immediately which can be handled using the catch() method </mark>

```js
let promise1 = new Promise((resolve, reject) => {
    setTimeout( () => {
        console.log("First promise is resolved");
        resolve(10);
    }, 1000)
})

let promise2 = new Promise((resolve, reject) => {
    setTimeout( () => {
        console.log("Second promise is resolved");
        resolve(20);
    }, 2000)
})

let promise3 = new Promise((resolve, reject) => {
    setTimeout( () => {
        console.log("Third promise is resolved");
        resolve(30);
    }, 3000)
});

Promise.all([promise1, promise2, promise3])
        .then(results => {
            const total = results.reduce((curr, temp) => curr+temp);
            console.log(results); // [10, 20, 30]
            console.log(total); // 60
        })
        .catch(error => console.log(error))

Promise.race([promise1, promise2, promise3])
        .then(result => console.log("RESOLVED : ", result)) // It resolves with RESOLVED : 10
```
## Promise.race()
The Promise.race(iterable) method returns a new promise that fulfills or rejects as soon as one of the promises in an iterable fulfills or rejects, with the value or error from that promise.


## Promise.any()
The Promise.any() method accepts a list of Promise objects as an iterable object. If one of the promises in the iterable object is fulfilled, the Promise.any() returns a single promise that resolves to a value which is the result of the fulfilled promise
