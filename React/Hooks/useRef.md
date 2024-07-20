Some typical use cases for using the native DOM API in the React world would include:
+ Manually focusing an element after it's rendered, like an input field in a form.
+ Detecting a click outside of a component when showing popup-like elements.
+ Manually scrolling to an element after it appears on the screen.
+ Calculating sizes and boundaries of components on the screen to correctly position something like a tooltip.

+ A Ref is just a mutable object that can store any value. That value will be preserved between re-renders.
+ A Ref's update doesn't trigger re-renders and is synchronous.
+ We can assign a Ref to a DOM element via the ref attribute. After that element is rendered, we'll see that element in the ref.current property.
+ We can pass Refs as regular props to any component. If we want to pass it as the actual ref prop, we need to wrap that component in forwardRef . Otherwise, it won't work on functional components. The second argument of that component will be the ref itself, which we then need to pass down to the desired DOM element.
