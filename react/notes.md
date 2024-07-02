# React

React self define as a library for web and native user interfaces, it is used to help devs to create user interfaces from reusable components, it's very useful to add interactivity in your application. React also have a big community and a lot of libraries and frameworks born around it, like Next.js and Remix.

## Refs

The important diference between ref from state, is that when we change a ref value, that ref does not cause your component to re-update.

```js
function Ref() {
  const rerenderCount = useRef(0);

  useEffect(() => {
    rerenderCount.current = rerenderCount.current + 1;
  });

  return <div>{rerenderCount.current}</div>;
}
```

The most common use case for refs in react is to reference a DOM element. because of how common this use case is every DOM element has a ref property tthat you can use for setting a ref to that element.

```js
function Component() {
  const inputRef = useRef(null);

  const focusInput = () => {
    inputRef.current.focus();
  };

  return (
    <>
      <input ref={inputRef} />
      <button onClick={focusInput}>Focus Input</button>
    </>
  );
}
```

## useEffect()

## Suspense

## Portals

## Error boundaries
