# React Concepts

## Components
Components are the building blocks of a React application. They are reusable pieces of UI that can be nested, managed, and handled independently.

```jsx
function Welcome(props) {
    return <h1>Hello, {props.name}</h1>;
}
```

In React every UI piece is a component, and each component has a state. React follows the observable pattern and listens for state changes. When the state of a component changes, React updates the virtual DOM tree. Once the virtual DOM has been updated, React then compares the current version of the virtual DOM with the previous version of the virtual DOM. This process is called “diffing”.

Once React knows which virtual DOM objects have changed, then React updates only those objects, in the real DOM. This makes the performance far better when compared to manipulating the real DOM directly. This makes React stand as a high-performance JavaScript library.

- [How does React use Virtual DOM](https://payalpaul2436.medium.com/10-main-core-concept-you-need-to-know-about-react-303e986e1763)



## JSX
JSX (JavaScript XML) is a syntax extension for JavaScript that looks similar to XML or HTML. It is used with React to describe what the UI should look like. JSX allows you to write HTML elements directly within JavaScript, making it easier to visualize the structure of the UI.

- **Embedding Expressions**: You can embed JavaScript expressions within JSX by wrapping them in curly braces `{}`.
- **Attributes**: JSX allows you to use attributes similar to HTML. However, some attribute names are different (e.g., `className` instead of `class`).
- **Children**: Elements can contain children, which can be other JSX elements or JavaScript expressions.

### Example:
```jsx
const element = <h1>Hello, world!</h1>;
```

In this example, `element` is a JSX element representing an `h1` HTML tag with the text "Hello, world!". This JSX code will be transpiled to JavaScript by tools like Babel, converting it into `React.createElement` calls that React can understand.

## Curly Braces
Curly braces `{}` are used in JSX to embed JavaScript expressions within the markup.

```jsx
const name = 'John';
const element = <h1>Hello, {name}</h1>;
```

## Fragments
Fragments let you group a list of children without adding extra nodes to the DOM.

```jsx
return (
    <React.Fragment>
        <ChildA />
        <ChildB />
    </React.Fragment>
);
```

## Props
Props are inputs to components. They are passed to components via HTML attributes and can be accessed within the component.

```jsx
function Welcome(props) {
    return <h1>Hello, {props.name}</h1>;
}
```

## Children
`props.children` is a special prop, automatically passed to every component, that can be used to render the content between the opening and closing tags of a component.

```jsx
function Wrapper(props) {
    return <div>{props.children}</div>;
}
```

## Keys
Keys help React identify which items have changed, are added, or are removed. They should be given to elements inside an array to give them a stable identity.

```jsx
const listItems = items.map((item) =>
    <li key={item.id}>{item.name}</li>
);
```

## Rendering
Rendering is the process of transforming your React components into DOM nodes that your browser can understand and display.

```jsx
ReactDOM.render(
    <App />,
    document.getElementById('root')
);
```

## Event Handling
React provides a way to handle events in a declarative way using event handlers.

```jsx
function handleClick() {
    alert('Button clicked!');
}

<button onClick={handleClick}>Click me</button>
```

## State
State is a built-in object that allows components to create and manage their own data.

```jsx
const [count, setCount] = useState(0);
```

## Controlled Components
Controlled components are those where form data is handled by the React component.

```jsx
function NameForm() {
    const [value, setValue] = useState('');

    const handleChange = (event) => {
        setValue(event.target.value);
    };

    return (
        <input type="text" value={value} onChange={handleChange} />
    );
}
```

## Hooks
Hooks are functions that let you use state and other React features in functional components.

```jsx
const [count, setCount] = useState(0);
```

## Purity
A pure component is one that does not cause side effects and returns the same output for the same input.

```jsx
function PureComponent({ value }) {
    return <div>{value}</div>;
}
```

## Strict Mode
StrictMode is a tool for highlighting potential problems in an application. It activates additional checks and warnings for its descendants.

```jsx
<React.StrictMode>
    <App />
</React.StrictMode>
```

## Effects
Effects let you perform side effects in function components.

```jsx
useEffect(() => {
    document.title = `You clicked ${count} times`;
}, [count]);
```

## Refs
Refs provide a way to access DOM nodes or React elements created in the render method.

```jsx
const inputRef = useRef(null);

useEffect(() => {
    inputRef.current.focus();
}, []);
```

## Context
Context provides a way to pass data through the component tree without having to pass props down manually at every level.

```jsx
const MyContext = React.createContext();

function MyProvider({ children }) {
    const value = { name: 'John' };
    return (
        <MyContext.Provider value={value}>
            {children}
        </MyContext.Provider>
    );
}
```

## Portals
Portals provide a way to render children into a DOM node that exists outside the DOM hierarchy of the parent component.

```jsx
ReactDOM.createPortal(
    <Child />,
    document.getElementById('portal-root')
);
```

## Suspense
Suspense lets you wait for some code to load and declaratively specify a loading state.

```jsx
const OtherComponent = React.lazy(() => import('./OtherComponent'));

<Suspense fallback={<div>Loading...</div>}>
    <OtherComponent />
</Suspense>
```

## Error Boundaries
Error boundaries are React components that catch JavaScript errors anywhere in their child component tree, log those errors, and display a fallback UI.

```jsx
class ErrorBoundary extends React.Component {
    constructor(props) {
        super(props);
        this.state = { hasError: false };
    }

    static getDerivedStateFromError(error) {
        return { hasError: true };
    }

    componentDidCatch(error, errorInfo) {
        // Log error
    }

    render() {
        if (this.state.hasError) {
            return <h1>Something went wrong.</h1>;
        }

        return this.props.children; 
    }
}
```

### References
- [Video - Every React Concept Explained in 12 Minutes](https://www.youtube.com/watch?v=wIyHSOugGGw)
- [Learn React – A Guide to the Key Concepts](https://www.freecodecamp.org/news/learn-react-key-concepts/)