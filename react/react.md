# React

## Creating A Project

To create a new React project with TypeScript, run the following command:

```lua
npx create-react-app <app_name> --template typescript
```

## Routing

### Installation

To use routing in React, install the react-router-dom library:

```
npm i react-router-dom
```

### Usage

#### Index.tsx

```typescript
root.render(
  <React.StrictMode>
    <BrowserRouter>
      <Routes>
        <Route path="/*" element={<App />} />
      </Routes>
    </BrowserRouter>
  </React.StrictMode>
);
```

#### Layout.tsx

```typescript
const Layout = () => {
  // Return the children routes
  return <Outlet />;
};

export default Layout;
```

#### Router.tsx

```typescript
const Router = () => {
  return(
    <Routes>
      // Parent route
      <Route path="/" element={<Layout />} >

        // Children routes of Layout
        <Route path = "/" element={<HomePage /> } />
      <Route />
    </Routes>
  )
}

export default Router;
```

### Path Parameters

#### Router.tsx

```typescript
const Router = () => {
  return(
    <Routes>
      // Parent route
      <Route path="/" element={<Layout />} >
        <Route path = "/collection/:id" element={<Collection /> } />
      <Route />
    </Routes>
  )
}

export default Router;

```

#### useParam Hook

```typescript
// Naming needs to match the specify path above
const { id } = useParam();
```

---

## Hooks

### useEffect

The useEffect hook runs at the start of a component lifecycle. It can be triggered multiple times via state dependency.

#### Not Dependent On State

```typescript
// Not dependent hence the empty array
useEffect(() => {
  console.log("I am not dependent on anyone!");
}, []);
```

#### Dependent On State

```typescript
const [foo, setFoo] = useState<number>(0);

// Will invoke whenever `foo` changes.
useEffect(() => {
  console.log("I am dependent on foo!");
}, [foo]); // foo is inside the array
```

---

## Context

### AuthProvider.tsx

```typescript
// A 'provider' allows us to pass state from one component to another

export const AuthContext = createContext<Auth | null>(null);
export const SetAuthContext = createContext<Function | null>(null);

// Like the name suggest, AuthProvider provides the auth and setAuth so you can use it
// in other components
const AuthProvider = ({ children }: any) => {
  const [auth, setAuth] = useState<Auth | null>(null);

  return(
    <AuthContext.Provider value={auth}>
      <SetAuthContext.Provider value={setAuth}>
        // The children are the components wrapped inside AuthProvider
        {children}
      </SetAuthContext>
    </AuthContext>
  )
};

export default AuthProvider;
```

### Using AuthProvider

#### Wrapping

```typescript
function App() {
  return (
    <div className="App">
      <AuthProvider>
        <Nav />
        <Router />
        <ToastContainer />
      </AuthProvider>
    </div>
  );
}

export default App;
```

#### Initializing AuthContext And SetAuthContext

```typescript
const auth = useContext<Auth | null>(AuthContext);
const setAuth = useContext<Function | null>(SetAuthContext);
```

---

## Useful Functions

### Spread Operator

```typescript
const auth: Auth = { ...r.data };
```

### Click Outside Close Dropdown

```typescript
const myRef = useRef<any>();
const [dropdown, setDropdown] = useState<boolean>(false);

useEffect(() => {
  let handler = (event) => {
    // If the click is not on the dropdown (anywhere outside of the dropdown)
    if (!myRef.current.contains(event.target)) {
      setDropdown(false);
    }
  };

  // Whenever the user clicks down on the page, it will create an event
  document.addEventListener("mousedown", handler);

  // Remove the event listener
  return () => {
    document.removeEventListener("mousedown", handler);
  };
});

return <div ref={myRef}></div>;
```