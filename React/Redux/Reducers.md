# What is Reducer
Whenever we dispatch an action to the store, it goes to a reducer.Reducers are pure functions, as the name suggests reducers take in two parameters one is <span style="font-style: italic; font-weight: bold"> CURRENT STATE </span> and other is ofcourse an <span style="font-style: italic; font-weight: bold"> ACTION </span>. Then it reduces into a single entity the new updated instance of state.

Once an action is dispatched all the REDUCERS are activated. Each reducer filters out the action using a switch statement switching on the action type. Whenever the switch statement matches with the action passed, the corresponding reducers take the necessary action to make the update and return a fresh new instance of the global state.

```js

const initialState = [
    {
        id : 1,
        todoText : "Buy Milk ",
        completed : true
    }
]

const todoReducer = (state=initialState, action) => {
    switch(action.type) {
        case "ADD_TODO" : return {
            ...state, 
            action.payload
        }

        case "DELETE_TODO" : {
            // Delete logic
            const newState = state.filter((todo)=> todo != action.payload.todo)
            return newState;
        }

        default : return state
    }
}
```

Note that the state parameter is a default parameter which accepts an initial state. This is to handle the scenario when the reducer is called for the first time when the state value is undefined.

(straight from chatGPT)</br>
Here are the key characteristics and responsibilities of reducers in Redux:

1. Pure Functions: Reducers must be pure functions, meaning they produce the same output for the same input and have no side effects. They should not modify the existing state but instead create a new state object with the desired changes.

2. State as an Immutable Object: Reducers work with the current state and return a new state object. They should not mutate the existing state. Immutability ensures that you can track changes to the state over time and helps prevent unintentional side effects.

3. State Initialization: Reducers typically provide an initial state when the application starts. This initial state defines the structure and default values for the state tree.

4. Handling Actions: Reducers receive actions as the second argument. Based on the action's type and, optionally, its payload, reducers determine how the state should be updated. Reducers should be designed to handle various action types and return the updated state accordingly.