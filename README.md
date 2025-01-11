# React

## Components
+ Rendering -  components rerender when props or state update
+ Pass `children` as a prop, to prevent rendering of children components when the parent component rerenders.

## Hooks
+ `useState` use to declare component state variables of any type. The initial (state) value is ignored on after the initial rendering. If using a function as a initializer, make sure the function is pure, has no arguments and returns a value (any type). The `useState` hook is async, meaning the changes do not take place right away when using the `set` function, in this case `setCounter`. 
  + https://react.dev/reference/react/useState
  + Declaration of component variables
```javascript
    const [counter, setCounter] = useState(0);
```
  + Declaration of component variable as a function
```javascript
const [counter, setCounter] = useState(() => {
        return 1 - 1
    });
```
  + Modifying values (good practice to use a updater function with the value (`pending state` in this case `counter`) and use it in the return as the `next state`.  This way you make sure the value gets updated in the already running code.
```javascript
setCounter((counter) => counter + 1)
```
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
  + Executes on unmount (clean up purposes)
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
