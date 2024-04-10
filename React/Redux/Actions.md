## What are Actions ? 
Actions are plain js object which describes events that changes the state of an application for ex it can be clicking a button, submitting a form etc. They are a fundamental part of the Redux architecture and are used to describe what should happen in response to user interactions or other events in your application. Actions are used to communicate the intent to modify the application's state to Redux. It is an object which consist of two things 

```js
{
    type: "SOME_USER_ACTION",
    payload: data related to the action
}
```

1. TYPE :- A string property that describes the nature or purpose of the action. Action types are typically defined as constants to ensure consistency and prevent typos. For example:

```js 
const ADD_TODO = 'ADD_TODO';
const REMOVE_TODO = 'REMOVE_TODO';
const UPDATE_USER = 'UPDATE_USER';
```

2. PAYLOAD :- The payload property is optional but is often used to include any data or information required to carry out the action. For instance, if you have an action to add a new item to a list, the payload might contain the details of the item being added.

```js 
{
    type: "ADD_TODO",
    payload : {
        id : 2,
        todo : "Buy milk",
        completed : false  
    }
}
```

Actions are produced by functions called action creators that in turn returns a js object which describes the purpose of the action like the object above. To update the state of your Redux store, you dispatch actions using the dispatch function provided by Redux. Dispatching an action is the process of sending the action object to the Redux store, which then uses reducers to update the state based on the action's type and payload.

```js

const dispatch = useDispatch();

const addTodo = () => {
    return {
        type: "ADD_TODO",
        payload : {
            id : 2,
            todo : "Buy milk",
            completed : false  
        }
    }
}

<button onClick={()=>dispatch(addTodo())}> ADD TODO </button>

```