# React

## Hooks
+ `useEffect` executes as the component mounts, unmounts and rerenders depending on dependencies passed.
  + execute only on mount (the dependency is an empty array `[]`)
```javascript
useEffect(() => {
        console.log('App Refresh')
    }, []);
```
