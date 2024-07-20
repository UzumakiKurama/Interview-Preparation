# useReducer 

useReducer hooks is used when you are handling multiple states in a component which are related to each other in some manner. Also it hides/abstracts the state management logic.


```js
const INITIAL_STATE = {
  counter : 0
}

const counterReducer = (state, action) => {
  switch(action.type){
    case "INCREMENT" : return {
      counter : state.counter + 1
    };
   
    case "DECREMENT" : return {
      counter : state.counter - 1
    };
    
    default : return state;
  }
}

const App = () => {
  
  const [state, dispatch] = React.useReducer(counterReducer, INITIAL_STATE)
  
  return <div className="flex-container">
      <button 
        onClick={() => dispatch({type : "INCREMENT"})}> 
        Increment       
      </button>
        {state.counter}
      <button 
        onClick={() => dispatch({type : "DECREMENT"})}> 
        Decrement 
      </button>
    </div>
}

ReactDOM.render(<App />, document.getElementById('app'));
```