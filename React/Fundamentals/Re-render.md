# All about re-renders 

+ Re-rendering is how react updates it's components with new data. It's what makes our component interactive
+ Whenever there is a change in the state of a component there will be a re-render, state update is the source of re-rendering. 
+ Props change doesn't initiate a re-render, only if the component is wrapped with React.Memo then props change will lead to re-render. 
+ We can use the pattern known as "moving state down" to prevent unnecessary re-renders in big apps