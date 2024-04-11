# Inheritance 
As we already know objects in javascript has a default hidden property called prototype which is either null or references another object. Prototypal inheritance uses prototype to extend an object's properties to another object. For example let's consider a Employee function :- 

```js
function employee(name, age){
    this.name = name;
    this.age = age;
}
```

Now a company can have sales, marketing, accounting employees which can inherit the above emplopyee function properties 

```js
function employeeDepartment(name,age,department){
    employee.call(this, name, age);
    this.department = department;
}

// To inherit the employee function 
Object.setPrototypeOf(employeeDepartment.prototype, employee.prototype);

// To see the prototype of employeeDepartment
console.log(employeeDepartment.prototype); // employee {constructor: ƒ}


console.log(Object.getPrototypeOf(employeeDepartment.prototype)); ////{getName: ƒ, constructor: ƒ}

const Abhijeet = employeeDepartment("Abhijeet", 23, "Engineering");
//At this point we can guess the output 
console.log(Abhijeet.name);
console.log(Abhijeet.age);
console.log(Abhijeet.department);

```
In class terms, this is equivalent to using the extends syntax.
Inheritance using ES6 Class is just syntatical sugar over prototypal inheritance. It adds a level of abstraction over prototype.

## Summary 
1. In JavaScript, all objects have a hidden [[Prototype]] property that’s either another object or null.
2. We can use obj.__proto__ to access it (a historical getter/setter, there are other ways, to be covered soon).
3. The object referenced by [[Prototype]] is called a “prototype”.
4. If we want to read a property of obj or call a method, and it doesn’t exist, then JavaScript tries to find it in the prototype.
5. Write/delete operations act directly on the object, they don’t use the prototype (assuming it’s a data property, not a setter).
6. If we call obj.method(), and the method is taken from the prototype, this still references obj. So methods always work with the current object even if they are inherited.
7. The for..in loop iterates over both its own and its inherited properties. All other key/value-getting methods only operate on the object itself.