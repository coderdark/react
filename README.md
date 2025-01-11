# React

## Hooks
+ `useEffect` executes as the component mounts, unmounts and rerenders depending on dependencies passed.
  + Execute only on mount (the dependency is an empty array `[]`)
```javascript
useEffect(() => {
        console.log('App Refresh')
    }, []);
```
  + Executes on mount and rerendering (the dependency has an element in the array)
```javascript
 const [user, setUser] = useState('No Name');

    useEffect(() => {
        console.log('App Refresh')
    }, [user]);
```
