# Deep Copy and Shallow Copy

There are two ways to clone an object in javascript : - 

+ Shallow Copy :- Where only the first level of object is copied and the deeper levels are copied as reference . Can be achieved using spread operator or Object.assign();
    + Changing the first level of object does not change the properties of  original object
    + Updating the deeper levels of the copied object changes the original object also as deeper levels are copied as reference.
+ Deep Copy :- Where the deeper levels of object are also copied.
    + After updating a property at any levels of the cloned objects, the original property is not updated.
    + A deep copy can be achieved using JSON.parse() + JSON.stringify():

```js
// Shallow Copy 
const originalObject = {
    name : "Abhijeet",
    age : 24,
    address : {
        city: "Balasore",
        state : "Odisha"
    }
}

const shallowCopy = { ...originalObject };
shallowCopy.name = "Satyajeet"
shallowCopy.address.city = "Cuttack"

console.log(originalObject) 
/* {
    name : "Abhijeet",
    age : 24,
    address : {
        city: "Cuttack",
        state : "Odisha"
    }
} */

console.log(shallowCopy);
/* {
    name : "Satyajeet",
    age : 24,
    address : {
        city: "Cuttack",
        state : "Odisha"
    }
} */


// Deep Copy
const origCopy = {
    name : "Abhijeet",
    age : 24,
    address : {
        street : {
            address_line1 : "Some value ....",
            address_line2 : "Also some value ....",
        },
        city: "Balasore",
        state : "Odisha"
    }
}

const deepCopy = JSON.parse(JSON.stringify(origCopy));

deepCopy.address.street.address_line1 = "Street no 23";

console.log(origCopy)
console.log(deepCopy);

/* {
  name: 'Abhijeet',
  age: 24,
  address: {
    street: {
      address_line1: 'Some value ....',
      address_line2: 'Also some value ....'
    },
    city: 'Balasore',
    state: 'Odisha'
  }
}
{
  name: 'Abhijeet',
  age: 24,
  address: {
    street: {
      address_line1: 'Street no 23',
      address_line2: 'Also some value ....'
    },
    city: 'Balasore',
    state: 'Odisha'
  }
} */
```

# Rest and Spread operator
Rest operator is used to destructure an array and apply some variables to some of the values in the array. The rest operator should always be the last value in the list af the array.
+ Rest parameters are used to create functions that accept any number of arguments.
+ The spread syntax is used to pass an array to functions that normally require a list of many arguments.

```js
// Rest Operator
let [naruto, sasuke, ...otherShinobi] = ["Naruto Uzumaki", "Sasuke Uchiha", "Sakura", "Lee", "Shikamarum", "Ino", "Hinata", "Neji"
 ]

 console.log(naruto) // Naruto Uzumaki
 console.log(sasuke) // Sasuke Uchiha
 console.log(otherShinobi) // [ 'Sakura', 'Lee', 'Shikamarum', 'Ino', 'Hinata', 'Neji' ]

//Spread Operator
let obj = { a: 1, b: 2, c: 3 };

let objCopy = { ...obj };

```

# this keyword

this keyword refers to the object that is calling a function in which this keword is used. It's value is determined dynamically at runtime and depends on the context in which the function is executed. 

1. Outside the functions this refers to the <mark>global object i.e the [window].
2. Regular functions (functions declared using function keywords) refer to the global window as the execution context.
3. Method calls use the calling object as their execution context.
4. How this is bound depends on how a function is invoked rather than on where it’s defined.