# useMemo 
The fundamental idea with useMemo is that it allows us to “remember” a computed value between renders.

    Wrap functions with useCallback when:

    React.memo()-wrapped component accepts a callback function as a prop
    - Passing a callback function as a dependency to other Hooks (i.e., useEffect)
    
    Use useMemo when:
    - For expensive calculations that should be cached when unrelated re-renders happen
    - Memoizing a dependency of another Hook
    
    A callback works well when code would otherwise be recompiled with every call. Memoizing results can help decrease the cost of repeatedly calling functions when the inputs change gradually over time. On the other hand, in the trading example, we may not want to memoize results for a constantly changing order book.