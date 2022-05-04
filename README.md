# useToggle

```tsx
const useToggle = () => useReducer((toggled) => !toggled, true)
```

# useClickOutside
```tsx
const useClickOutside = (ref: RefObject<Node>, callback: () => void) => {
  useEffect(() => {
    const handleClick = (event: MouseEvent) => {
      if (
        ref.current &&
        event.target instanceof Node &&
        !ref.current.contains(event.target)
      ) {
        callback()
      }
    }

    window.addEventListener("click", handleClick, true)

    return () => {
      window.removeEventListener("click", handleClick, true)
    }
    // callback is a function so on every render it'll be recreated and useEffect will be called again
    // for sake of optimization you can wrap outer callback in useCallback
  }, [ref, callback])
}
```
