# Next

## Create A Project

`npx create-next-app@latest my-project --ts`

## Routing

### Navigating From Element

```typescript
<Link href="/your-path"></Link>
```

### Creating Routes

Under the page/ make a directory to the name of the path. Inside the created dir, make a file call index.tsx. Next Js is smart enough to map the folder and index.tsx as the path

#### Login Route Example

`pages/login/index.tsx`

#### Register Route Example

`pages/register/index.tsx`

## Headless UI

`npm i @headlessui/react`

Headless UI works the best with Tailwindcss. Use Healdess UI for transition animation.

```typescript
<Transition
  show={isOpen}
  enter="ease-out transition duration-300"
  enterFrom="transform opacity-0"
  enterTo="transform opacity-100"
  leave="ease-in transition duration-300"
  leaveFrom="transform opacity-100"
  leaveTo="transform opacity-0"
>
  <Component />
</Transition>
```

## Creating A Modal

### Blur Out Background

Make a div to wrap the modal. This div is for blurring out the background

**NOTE:** If the modal is a child element, the parent element make have overflow-visible, so the child can overlap the parent

```typescript
<div className="absolute | bg-gray-500 backdrop-blur-sm | w-full h-full | top-0 left-0">
  {modal}
</div>
```
