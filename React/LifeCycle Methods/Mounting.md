# Mounting
When a component first appeard on the screen, it is known as mounting. This is when React creates this component's instance for the first time, initializes its state, runs its hooks, and appends elements to the DOM.
The end result - we see whatever we render in this component on the
screen.

Below lifecycles are called in following order during the mounting phase :- 

 ## Constructor
It's feature of class based components, and not something special that react provides. You use it to initialize the component's state and bind methods to the component's instance

## static getDerivedStateFromProps(nextState, prevProps)
The method should return an object that represents the updated state of the component, or null if no state update is necessary.

It's important to note that getDerivedStateFromProps() is a static method, which means it does not have access to the this keyword and cannot interact with the component's instance methods or properties.
This method us not used anymore in the latest version of React.

## render()
It constructs the components's virtual DOM representation, it is responsible for printing components on screen. This lifecycle is called everytime there is a change in props or state. At this point everthing is mounted and visible on screen. 

## componentDidMount()
This lifecycle method is used to perform actions like DOM manipulation, external api requests, event listeners etc. It is triggered only once after the component gets rendered on screen.


 ```js
class Employer extends React.Component {
    constructor(props){
        super(props); 
        // Super method is use to call the constructor of its parent's  class to access the properties and methods of its parent i.e its calling the constructor of React.Component class

        this.state = {
            name:"",
            phone:"",
        }

        console.log("1-constructor");
    }

    static getDerivedStateFromProps(){
        console.log("2-getDerivedStateFromProps");
        return null;
    }

    componentDidMount(){

    }

    componentWillUnmount(){
        //This lifecycle is only triggered when the component is removed from DOM. 
    }

    render(){
        console.log("3-render")
        return(
            <div>Component Lifecycle</div>
        )
    }
}
 ```


