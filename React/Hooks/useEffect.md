# UseEffect
This hook mimics the functionality of lifecycle methods (which can only be used in class based components) inside functional components.

+ It accepts a setup function which contains the effect's logic. This function may or may not return a function which is known as cleanup function.
+ It accepts a dependency array as the 2nd argument. </br>

Caveats : -

    Examples of passing reactive dependencies
    1. If we pass a dependency array containing arguments that means our useEffect will run on the inital render and re-renders with changed dependencies
    2. Passing a empty dependecy array, the useEffect will run only for the inital render. 
    3. If we pass no array at all, useEffect will run for every render of our component. 
