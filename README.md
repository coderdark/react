# React

## Hooks
+ `useEffect` executes as the component mounts, unmounts and component state updates depending on the dependencies passed.
  + https://react.dev/reference/react/useEffect
  + Execute only on mount (the dependency is an empty array `[]`)
```javascript
import {useEffect, useState} from "react";

export default function App() {
    const [counter, setCounter] = useState(0);

    useEffect(() => {
        console.log('Component Mount, or State Update');
    }, []);

    return (<main>
        <p><span style={{fontWeight: 'bold'}}>App</span> {counter}</p>
        <button onClick={() => setCounter((counter) => counter + 1)}>Update</button>
    </main>);
}
```
  + Executes on mount and component state update (the dependency has the user in the array `[user]`, when user updates the component rerenders and teh useEffect is executed)
```javascript
import {useEffect, useState} from "react";

export default function App() {
    const [counter, setCounter] = useState(0);

    useEffect(() => {
        console.log('Component Mount, or State Update');
    }, [counter]);

    return (<main>
        <p><span style={{fontWeight: 'bold'}}>App</span> {counter}</p>
        <button onClick={() => setCounter((counter) => counter + 1)}>Update</button>
    </main>);
}
```
  + Executes on unmount
```javascript
import {useEffect, useState} from "react";

export default function App() {
    const [counter, setCounter] = useState(0);

    useEffect(() => {
        console.log('Component Mount, or State Update');

        return () => {
            console.log('Component Unmount or State Update');
        }
    }, [counter]);

    return (<main>
        <p><span style={{fontWeight: 'bold'}}>App</span> {counter}</p>
        <button onClick={() => setCounter((counter) => counter + 1)}>Update</button>
    </main>);
}
```
