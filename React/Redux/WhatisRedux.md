# Redux
Redux is a read-only state management library. It is mostly used in conjunction with react but it's not limited to react, can be used with other frontend libraries also like Vue, Angular etc.

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