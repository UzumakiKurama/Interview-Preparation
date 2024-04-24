# Higher Order Components (HOC)

+ HOC's are functions that accepts a component and returns a new component with augmented behaviour. This allows developers to wrap existing components with aditional features such as state management, authentication logic, or data fetching capabilites without changing the original component  
+ HOCs allow you to reuse component logic across multiple components, which can save time and reduce code duplication.
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