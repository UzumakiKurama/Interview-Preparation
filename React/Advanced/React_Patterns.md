# Higher Order Components (HOC)

+ HOC's are functions that accepts a component and returns a new component with augmented behaviour. This allows developers to wrap existing components with aditional features such as state management, authentication logic, or data fetching capabilites without changing the original component  
+ HOCs allow you to reuse component logic across multiple components, which can save time and reduce code duplication.
+ HOC's are mostly used for authenticating routes, logging functionality, styling and theming etc
+ HOCs should be kept stateless and pure for maximum reusability and performance. Less baggage, more fun!
+ Below is an example of HOC component which can be used for lifecycle logging :- 

```js
const HOCWrapper = (WrappedComponent) => {
  class augmentedComponent extends React.Component {
    componentDidMount() {
      console.log(`${WrappedComponent.name} has mounted`);
    }
    componentWillUnmount() {
      console.log(`${WrappedComponent.name} has unmounted`);
    }

    render() {
      return <WrappedComponent {...this.props} />;
    }
  }

  return augmentedComponent;
};
```

```js
import "./styles.css";
import OrigComponent from "./OrigComonent";
import HOCWrapper from "./HOC";

const OrigComponent = (props) => {
  return (
    <div>
      <span> {`Hello ${props.name}`} </span>
    </div>
  );
};

const NewComponent = HOCWrapper(OrigComponent);

export default function App() {
  return (
    <div className="App">
      <NewComponent name="Abhijeet" />
    </div>
  );
}
```

# Render Props
+ At its essence, the Render Props pattern is a technique for sharing code between React components using a prop whose value is a function. This function, often called the "render prop," enables components to share not just UI elements but also rendering logic.
+ By passing a function as a prop to a component, developers can delegate control over the rendering logic to the parent component, enabling a more dynamic and customizable behavior.
+ Employee is a component which accepts a function (render) as a prop, this function prop can be used to conditionally render UI.

```js
const employees = [
    {
        id : 1,
        name : "Abhijeet Behera",
        role : "Frontend Developer"
    },
    {
        id : 2,
        name : "Raju Chacha",
        role : "Backend Developer"
    },
    {
        id : 3,
        name : "Babu Bhaiya",
        role : "Quality Assurance Engineer"
    }
]

const Employee = ({render}) => {
    return <>{render(employees)}</>;
}
```
+ On one component HomePage we are only rendering names of the employees while on the second component EmpPage we are rendering whole employee data.
```js
const HomePage = () => {
    return (
        <Employee render={(employees)=>(
            <div>
                {
                    employees?.map(emp => <span>{emp.name}</span>)
                }
            </div>
        )} />
    )
}

const EmpPage = () => {
    return (
        <Employee render={employees => (
            <div>
                {
                    employees?.map(emp => (
                        <ul>
                            <li>{emp.id}</li>
                            <li>{emp.name}</li>
                            <li>{emp.role}</li>
                        </ul>
                    ))
                }
            </div>
        )}>
    )
}
``` 
# Custom Hooks 
+ Custom Hooks are a React feature that allows developers to extract and reuse stateful logic from components. Unlike traditional React components, Custom Hooks are functions whose names typically start with "use," and they can leverage other built-in hooks such as useState or useEffect or even other Custom Hooks.

```js
import { useState, useEffect } from 'react';
const useFetch = (url) => {
    const [data, setData] = useState(null);
    const [loading, setLoading] = useState(true);
    const [error, setError] = useState(null);

    useEffect(() => {
            const fetchData = async () => {
                try {
                    const response = await fetch(url);
                    const result = await response.json();
                    setData(result);
                } catch (error) {
                    setError(error);
                } finally {
                    setLoading(false);
                }
            };
fetchData();
    }, [url]);
return { data, loading, error };
};
```