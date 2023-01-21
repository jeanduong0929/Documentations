# React

## Creating A Project

`npx create-react-app <app_name> --template typescript`

## Routing

### Install library

`npm i react-router-dom`

### Example

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

```ts
const Layout = () => {
  return <Outlet />;
};

export default Layout;
```

#### Router.tsx

```ts
const Router = () => {
  return(
    <Routes>
      <Route path="/" element={<Layout />} >
        <Route path = "/" element={<HomePage /> } />
      <Route />
    </Routes>
  )
}

export default Router;
```
