+ With Context (or any context-like state management library), we can pass data directly from one component to another deep in the render tree without the need to wire it through props.
+ Passing data in this way can improve the performance of our apps, as we'll avoid the re-rendering of all components in between.

+ Context, however, can be dangerous: all components that use it will re-render if the value in the Context provider changes. This re-render can't be stopped with standard memoization techniques.

+ To minimize Context re-renders, we should always memoize the
value we pass to the provider.

+ We can split the Context provider into multiple providers to further minimize re-renders. Switching from useState to
useReducer can help with this.

+ Even though we don't have proper selectors for Context, we can
imitate their functionality with higher order components and
React.memo.