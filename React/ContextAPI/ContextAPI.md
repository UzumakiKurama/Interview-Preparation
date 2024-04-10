# Context API
The MyContext object will hold all the data that is going to be shared through the application. 

```js
import { createContext } from 'react';

export const MyContext = createContext("");
```

Now we need to wrap the components where this data is going to be shared using a provider component. The Provider component accepts a "value" prop that holds the shared data, and any component that is a child of the Provider component can access that shared data. Usually we wrap the [[<App/]] component, the top most level component
```js
import { useState, React } from "react";
import { MyContext } from "./MyContext";
import MyComponent from "./MyComponent";

function App() {
  const [text, setText] = useState("");

  return (
    <div>
      <MyContext.Provider value={{ text, setText }}>
        <MyComponent />
      </MyContext.Provider>
    </div>
  );
}

export default App;
```

Now we need to consume the context inside the Mycomponent

```js
import { useContext } from 'react';
import { MyContext } from './MyContext';

function MyComponent() {
  const { text, setText } = useContext(MyContext);

  return (
    <div>
      <h1>{text}</h1>
      <button onClick={() => setText('Hello, world!')}>
        Click me
      </button>
    </div>
  );
}

export default MyComponent;
```