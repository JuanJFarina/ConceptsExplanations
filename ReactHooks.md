## React Hooks

React Hooks are functions that allow you to use state and other React features in functional components without writing a class. They provide a simpler and more concise way to manage state, side effects, and other React features.

### useState

The `useState` hook is used to manage state in functional components. It returns a pair of values: the current state and a function to update it. Typical use cases include managing form inputs, toggling UI elements, and handling component-specific state.

### useEffect

The `useEffect` hook is used to perform side effects in functional components. It runs after every render and can be used to fetch data, subscribe to events, or update the DOM. Typical use cases include fetching data from an API, setting up event listeners, and cleaning up resources.

### useContext

The `useContext` hook is used to access the value of a context in functional components. It allows you to consume context values without wrapping your components in context providers. Typical use cases include accessing theme settings, user authentication, and localization data.

### useReducer

The `useReducer` hook is used to manage complex state logic in functional components. It is an alternative to `useState` and is helpful when state transitions involve multiple sub-values or complex state updates. Typical use cases include managing state with complex business logic, handling form validation, and implementing undo/redo functionality.

### useMemo

The `useMemo` hook is used to memoize expensive computations in functional components. It takes a function and a dependency array, and returns the memoized value. It helps optimize performance by avoiding unnecessary re-computations. Typical use cases include memoizing derived data, optimizing heavy calculations, and preventing unnecessary renders.

### useCallback

The `useCallback` hook is used to memoize callback functions in functional components. It returns a memoized version of the callback function, optimizing performance by preventing unnecessary re-renders of child components. Typical use cases include optimizing event handlers, preventing unnecessary renders in child components, and passing callbacks to optimized child components.

### useRef

The `useRef` hook is used to create mutable references in functional components. It returns a mutable ref object with a `.current` property. It can be used to store values between renders, access DOM nodes, and preserve values across function calls. Typical use cases include accessing DOM elements, storing previous values, and interacting with third-party libraries.

### custom hooks

Custom hooks are reusable functions that encapsulate common logic and stateful behavior. They allow you to extract component logic into reusable functions, promoting code reuse and maintainability. Typical use cases include abstracting API calls, managing complex form state, and encapsulating business logic.
