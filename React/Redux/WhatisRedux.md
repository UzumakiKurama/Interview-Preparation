# Redux
Redux is a pattern and library for managing and updating application state, using events called "actions". It serves as a centralized store for state that needs to be used across your entire application, with rules ensuring that the state can only be updated in a predictable fashion.

In simpler terms redux can be thought of as a centralized store which keeps all the application data that can be accessed by any component.

![Redux](redux)

<span style="color: red; font-size: 16px "> 

Core components of Redux are store , actions and reducers .<br/>

[What is store](redux)<br/>
[What is Action](./Actions.md)<br/>
[What is Reducer](./Reducers.md)<br/>

</span>

In short, the following three principles completely govern how Redux works:

+ The global state of an application is stored in an object tree within a single store
+ The only way to change the state is to emit an action, which is an object describing what happened
+ To specify how the state tree is transformed by actions, we write pure reducers
+ Time-travel debugging: You can trace every action that has occurred in the application and see how the state has changed over time.