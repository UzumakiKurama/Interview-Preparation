# UseCallback
```js
const Component = () => {
    const submit = () => {/* Does Something */}
    
    const memoizedSubmit = useCallback(() => {}, [])

    useEffect(() => {
        // something happens
    }, [submit])

    return (..)
}
```
Looking at the code above the useEffect hook will run on every re-render even though we have mentioned submit as an dependency which should mean that useEffect hook should only execute if the submit function changes. But it does change and that's why the useEffect hook will re-render itself at every re-render. 

React uses shallow comparison to compare the dependencies, here the submit function is an object which contains a reference to the memory where the actual function is store. Everytime the componenet re-renders a new submit function is created and hence a new refernce is also created. That's why the comparsion of dependencies here will always be false.

    This can be resolved by using the useCallback hook, just wrap the callback in useCallback and it will always return the memoized reference 

Use cases of useCallback 

+ As explained above most widely use case of this is to wrap dependecy objects 
+ Another use case is to wrap props, but only wrap those props which are used as an dependency in some downstream component. 
+ It is also used with React.memo() to wrap props which are not primitive data types.

```js
const MemoChild = () => React.memo(Child);

/* In this case if Parent is re-rendered the MemoChild component will not be re-rendered because it's props did not change */
const Parent = () => {

    return (
        <MemoChild id="1" />
    )
}

// In this case the MemoCHild will get re-rendered because comparison of props will give false ..so in this case wrap prop in useCallback() or useMemo()
const Parent = () => {

    return (
        <MemoChild id="1" data={{name : "Lamb"}} />
    )
}

//Memoization is broken in the below example as the div element is just a children prop. If we are providing childrens to a memoized component. that should also be wrapped in a useCallback or useMemo

const Parent = () => {

    return (
        <MemoChild>
            <div>Something</div>
        </MemoChild>
    )

    const Children = useMemo(() =><div>Something</div>, [])
    return (
        <MemoChild>{Children}</MemoChild>
    )
}

```
