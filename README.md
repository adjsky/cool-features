# useToggle

```tsx
const useToggle = (initialValue = false) =>
  useReducer((toggled) => !toggled, initialValue)
```

# useClickOutside
```tsx
const useClickOutside = (ref: RefObject<Node>, callback: () => void) => {
  useEffect(() => {
    const handleClick = (event: PointerEvent) => {
      if (
        ref.current &&
        event.target instanceof Node &&
        !ref.current.contains(event.target)
      ) {
        callback()
      }
    }

    window.addEventListener("pointerdown", handleClick, true)

    return () => {
      window.removeEventListener("pointerdown", handleClick, true)
    }
    // callback is a function so on every render it'll be recreated and useEffect will be called again
    // for sake of optimization you can wrap outer callback in useCallback
  }, [ref, callback])
}
```
