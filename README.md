# React

## Hooks
+ `useEffect` executes as the component mounts, unmounts and component state updates depending on the dependencies passed.
  + Execute only on mount (the dependency is an empty array `[]`)
```javascript
useEffect(() => {
        console.log('App Refresh')
    }, []);
```
  + Executes on mount and component state update (the dependency has the user in the array `[user]`, when user updates the component rerenders and teh useEffect is executed)
```javascript
 const [user, setUser] = useState('No Name');

    useEffect(() => {
        console.log('App Refresh')
    }, [user]);
```
