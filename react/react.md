# React

## Creating A Project

`npx create-react-app <app_name> --template typescript`

---

## Routing

### Install library

`npm i react-router-dom`

### How To Use

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
    if (!myRef.current.contains(event.target.value)) {
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
