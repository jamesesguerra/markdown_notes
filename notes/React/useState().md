---
tags: [Notebooks/React, React Hooks]
title: useState()
created: '2022-07-15T13:46:30.473Z'
modified: '2022-08-06T05:54:25.064Z'
---

# useState()

### Allows you to maintain state between renders:
```js
const [state, setState] = useState(initialValue);
```

### When calculating new state based on the value of the previous state:
```js
setState((prevState) => {
  return prevState + 1;
});
```

### When using an expensive function to compute for the initial state:
```js
// is only run once, on the initial render
const [count, setCount] = useState(() => foo());

// ❌ runs every time the component is re-rendered
const [count, setCount] = useState(foo());
```

### Immutability
```js
const [state, setState] = useState({ id: 1, name: 'Name' });

// update state by spreading the previous state
setState({ ...state, name: 'Updated Name' })
```
