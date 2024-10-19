### 1. **What is React.js?**
React.js is an open-source JavaScript library for building user interfaces, primarily for single-page applications. It allows developers to build reusable UI components and manage the state efficiently. It’s maintained by Facebook and is widely used for its fast rendering with the Virtual DOM.

### 2. **Difference between Virtual DOM, Shallow DOM, and DOM in React.js**
- **DOM**: The Document Object Model (DOM) represents the UI of your application as a tree of nodes. However, updating the real DOM is slow.
- **Virtual DOM**: React creates a lightweight copy of the real DOM. When a change occurs, React updates the Virtual DOM first and compares it with the real DOM (using a diffing algorithm). Only the changed elements are re-rendered.
- **Shallow DOM**: It refers to testing only the immediate children of a component, unlike deep rendering that tests all children components.

### 3. **What is a Controlled and Uncontrolled Component in React.js?**
- **Controlled Components**: In controlled components, the form data is handled by the React component. Here, the input field’s value is managed by the component’s state.
  ```js
  function MyForm() {
    const [value, setValue] = useState("");
    return (
      <input value={value} onChange={(e) => setValue(e.target.value)} />
    );
  }
  ```
- **Uncontrolled Components**: In uncontrolled components, the form data is handled by the DOM itself.
  ```js
  function MyForm() {
    const inputRef = useRef();
    return <input ref={inputRef} />;
  }
  ```

### 4. **What are Hooks in React.js?**
Hooks are functions that let you use state and lifecycle methods in functional components.
- **useState**: Manages state in a functional component.
- **useEffect**: Manages side effects like data fetching or DOM manipulation.
- **useMemo**: Memoizes expensive calculations.
- **useCallback**: Memoizes callback functions to prevent unnecessary re-rendering.

### 5. **What is JSX, Babel, Webpack?**
- **JSX**: JavaScript XML, a syntax extension that allows mixing HTML with JavaScript. It’s used to describe UI in React.
  ```js
  const element = <h1>Hello, world!</h1>;
  ```
- **Babel**: A JavaScript compiler that converts JSX into plain JavaScript.
- **Webpack**: A module bundler that bundles all JavaScript files and assets like images, CSS into one file for use in the browser.

### 6. **What is Redux?**
Redux is a predictable state container for JavaScript apps. It helps manage the state of the app by maintaining a single source of truth (store).

### 7. **What are Reducers, Actions, and Store in Redux?**
- **Action**: An object that describes the changes you want to make.
  ```js
  const incrementAction = { type: "INCREMENT" };
  ```
- **Reducer**: A pure function that takes the current state and an action and returns the new state.
  ```js
  function counter(state = 0, action) {
    switch (action.type) {
      case "INCREMENT":
        return state + 1;
      default:
        return state;
    }
  }
  ```
- **Store**: The object that holds the state of the entire application.
  ```js
  const store = createStore(counter);
  ```

### 8. **What is Middleware in Redux?**
Middleware is a function that allows you to intercept actions before they reach the reducer. Common middlewares are Redux Thunk and Redux Saga.

### 9. **Explain Data Flow in Redux**
Redux follows a unidirectional data flow:
1. **Action** is dispatched.
2. **Reducers** update the state based on the action.
3. The **Store** saves the new state and updates the UI.

### 10. **What is Redux Thunk?**
Redux Thunk is a middleware that allows you to write action creators that return a function instead of an action, enabling asynchronous logic like API calls.
```js
const fetchData = () => {
  return (dispatch) => {
    fetch('/api/data')
      .then(response => response.json())
      .then(data => dispatch({ type: 'FETCH_DATA_SUCCESS', payload: data }));
  };
};
```

### 11. **What is Redux Saga? Difference between Redux Thunk and Redux Saga**
Redux Saga is a middleware library for managing side effects in Redux, such as API calls. It uses generator functions to handle async actions more declaratively.
- **Redux Thunk** is simpler and uses functions to handle async logic.
- **Redux Saga** uses ES6 generators and handles more complex async flows.

### 12. **Difference between Class Component and Function Component**
- **Class Components**: Use `class` syntax and have lifecycle methods like `componentDidMount`.
  ```js
  class MyComponent extends React.Component {
    render() {
      return <h1>Hello, World!</h1>;
    }
  }
  ```
- **Function Components**: Use functions and hooks like `useState`, `useEffect`.
  ```js
  function MyComponent() {
    return <h1>Hello, World!</h1>;
  }
  ```

### 13. **How to Implement componentWillUnmount in Function Component**
You can use the `useEffect` hook with a cleanup function to mimic `componentWillUnmount`.
```js
useEffect(() => {
  return () => {
    console.log("Component will unmount");
  };
}, []);
```

### 14. **useEffect, useState, useMemo, useCallback Hooks in Detail**
- **useEffect**: Manages side effects.
  ```js
  useEffect(() => {
    document.title = "New title";
  }, []);
  ```
- **useState**: Manages state.
  ```js
  const [count, setCount] = useState(0);
  ```
- **useMemo**: Memoizes expensive calculations.
  ```js
  const memoizedValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);
  ```
- **useCallback**: Memoizes a function.
  ```js
  const memoizedCallback = useCallback(() => {
    doSomething(a);
  }, [a]);
  ```

### 15. **Explain Lifecycle Methods in React.js**
Lifecycle methods are hooks into different phases of a React component's life:
- **Mounting**: `constructor`, `render`, `componentDidMount`
- **Updating**: `componentDidUpdate`
- **Unmounting**: `componentWillUnmount`

### 16. **Difference between `export default` and `export` in React.js**
- **export default**: Exports a single default export.
  ```js
  export default function MyComponent() {}
  ```
- **export**: Exports multiple named exports.
  ```js
  export const MyComponent = () => {};
  ```

### 17. **What is Portal in React.js?**
Portals provide a way to render children into a DOM node that exists outside the parent component’s DOM hierarchy.
```js
ReactDOM.createPortal(child, domNode);
```

### 18. **What is Reconciliation in React.js?**
Reconciliation is the process React uses to update the DOM by comparing the Virtual DOM with the real DOM and applying only the necessary changes.

### 19. **What is useRef in React.js?**
`useRef` allows you to persist values across renders or directly access a DOM element.
```js
const myRef = useRef(null);
```

### 20. **What is Server-Side Rendering in React.js?**
Server-side rendering (SSR) is the ability to render React components on the server before sending the HTML to the client. It improves SEO and performance.

### 21. **What is useStrict in React.js?**
`useStrict` in React enforces stricter coding standards and helps to identify potential problems early.

### 22. **What is Fragment in React.js?**
A fragment allows you to group multiple elements without adding extra nodes to the DOM.
```js
<React.Fragment>
  <div>Element 1</div>
  <div>Element 2</div>
</React.Fragment>
```

### 23. **What is React Router in React.js?**
React Router is a library for managing routing in a React application. It enables navigation between different components.

### 24. **What is node_modules in React.js?**
`node_modules` is a folder where all the project’s npm packages are installed.

### 25. **What is the Default Localhost Server Port in React.js? How Can We Change It?**
The default server port is `3000`. You can change it by specifying a different port in the `package.json` file:
```json
"scripts": {
  "start": "PORT=4000 react-scripts start"
}
```

### 26. **What is a Higher-Order Component in React.js?**
A Higher-Order Component (HOC) is a function that takes a component and returns a new component with added functionality.
```js
function withAuth(Component) {
  return function AuthenticatedComponent(props) {
    // logic here
    return <Component {...props} />;
  };
}
```

### 27. **What is a Pure Component in React.js?**
A Pure Component in React implements `shouldComponentUpdate` and only re-renders

 if props or state change.
```js
class MyPureComponent extends React.PureComponent {}
```

### 28. **What is the Difference Between State and Props in React.js?**
- **State**: Managed internally by the component and can change over time.
- **Props**: Passed down from parent components and are read-only.

### 29. **How to Optimize a React.js App?**
- Use React.memo and `useMemo` to prevent unnecessary re-renders.
- Use lazy loading for code-splitting.
- Optimize the number of renders using `shouldComponentUpdate`.

### 30. **What is the Difference Between React.js and Angular.js?**
- **React** is a library focusing on building UI, while **Angular** is a full-fledged framework with two-way data binding and more built-in features.

### 31. **What is Prop Drilling in React.js? How to Overcome It?**
Prop drilling is passing data through multiple layers of components. It can be overcome using **Context API** or **Redux** for centralized state management.

### 32. **What is Context API in React.js?**
Context API provides a way to pass data deeply throughout the component tree without having to pass props manually at every level.

### 33. **What is Super, Constructor, Render Function in React.js?**
- **super()** calls the constructor of the parent class.
- **constructor** initializes state and binds event handlers.
- **render** returns the JSX to be displayed.

---

Feel free to copy and paste this into your GitHub as-is!
