# useState

+ The most commonly used or the first hook that we learn in react is useState. It is used for state management in functional components. 
+ useState returns an array with exactly 2 values :
    + current state which matches your initial state
    + set function which is used to updated the value of the state
+ we can pass a function as a intial value in useState, it would be treated as a initializr function which will be called when initializing the component. This function should be pure and it should not take any arguments. 

```js 
import React, { useState } from 'react';

const [name, setName] = usestate('');
const [count, setCount] = useState(() => 0);

setName('Abhijeet');
setName(num => num+1);
```
+ The set function accepts nextState as the only argument. 
+ If you pass a function as nextState, it will be treated as an updater function. It must be pure, should take the pending state as its only argument, and should return the next state. React will put your updater function in a queue and re-render your component. During the next render, React will calculate the next state by applying all of the queued updaters to the previous 
+ The set function does not return any value