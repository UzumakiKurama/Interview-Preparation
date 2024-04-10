# Updating Phase
This phase takes place when there is some change in UI due to user actions, or it could be anyother actions such as a setTimeout function which changes the UI after some time interval. The following functions or lifecycles gets called in the below order :- 

## getDerivedStatesFromProps()
The getDerivedStateFromProps is a static method in React used for updating the state of a component based on changes in its props. It's a lifecycle method available in both class components and functional components (using React hooks) and is often used when you need to synchronize component state with incoming props.

## shouldComponentUpdate( nextProps, nextState )
This lifecycle gets called before the render function and after the getDerivedStatesFromProps lifecycles.
<span style="color:red; font-style:italic;"> This lifecycle must return a boolean value i.e. true or false which determines whether a component should update or not.
</span>

## getSnapshotBeforeUpdate(prevProps, prevState)
This method is used to capture some information from the DOM before it is potentially changed due to a component update. It is often used to save scroll positions or other UI-related data that needs to be preserved when an update occurs. We can save any values in this method which can be accessed by other lifecycle methods that are executed after this.

## componentDidUpdate( prevProps, prevState )
This lifecycle method  is called after a component has been updated and re-rendered. It is useful for performing side effects or additional operations when the component's props or state have changed.

