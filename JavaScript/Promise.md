# Promise
An object that is used as a placholder for the future result of an asynchornous operation.
<div style="text-indent: 23em"> OR </div>
A placeholder/container for future value such as a AJAX response.  

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