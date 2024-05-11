# Polyfills
New language features may include not only syntax constructs and operators, but also built-in functions.
For example, Math.trunc(n) is a function that “cuts off” the decimal part of a number, e.g Math.trunc(1.23) returns 1.

In some (very outdated) JavaScript engines, there’s no Math.trunc, so such code will fail. A script that updates/adds new functions is called “polyfill”. It “fills in” the gap and adds missing implementations.

## Polyfill for Array.map() 

```js
Array.prototype.customMap = function(fn){
    let tempArr = [];
    for(let i=0; i<this.length; i++){
        tempArr.push(fn(this[i], i, this));
    }
    return tempArr;
}

const nums = [1,2,3,4,5];
let result = nums.customMap((item) => item*2);
console.log(result); // [ 2, 4, 6, 8, 10 ]
```

## Polyfill for Array.filter() 
```js
Array.prototype.customFilter = function(fn){
    let tempArr = [];
    for(let i=0; i<this.length; i++){
        if(fn(this[i], i, this)) tempArr.push(this[i]);
    }
    return tempArr; 
}
const nums = [1,2,3,4,5];
console.log(nums.customFilter(item => item%2 == 1 )); // [ 1, 3, 5 ]
```

## Polyfill for Array.reduce()
```js
Array.prototype.customReduce = function(fn, initialValue=0){
    let result=initialValue;
    for(let i=0; i<this.length; i++){
        result = fn(result, this[i], i, this);
    }
    return result;
}

console.log(nums.customReduce((acc, curr) => acc - curr)); // -15
```
## Polyfill for Array.call(), Array.apply(), Array.bind()
```js
Function.prototype.customCall = function(obj, ...args){
    obj.fn = this;
    obj.fn(...args);
}

Function.prototype.customApply = function(obj, args){
    obj.fn = this;
    obj.fn(...args);
}

Function.prototype.customBind = function(obj, ...args){
    let obj = this;
    return function(...args2){
        obj.apply(obj, [...args, ...args2])
    }
}
```

## Polyfill for Promise.All()
```js
let promise1 = new Promise((res,rej) => {
    setTimeout(() => res(10), 2000);
});

let promise2 = new Promise((res,rej) => {
    setTimeout(() => rej(20), 4000);
})

let promise3 = new Promise((res,rej) => {
    setTimeout(() => res(30), 6000);
});

Promise.myAll = function(arr){
    const promise = new Promise((resolve, reject) => {
        let result = [];
        let total = 0;
        arr.forEach((pro, i) => {
            Promise.resolve(pro).then(res => {
                result[i] = res;
                total++;
                if(total === arr.length) resolve(result);
            }).catch(err => reject(err));
        })
    })
    return promise;
}

Promise.myAll([promise1, promise2, promise3])
    .then(res => console.log(res))
    .catch(err => console.log(err));
```
