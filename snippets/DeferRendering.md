---
title: Reduce Unnecessary Re-rendering
tags: components,hooks,rendering
cover: blog_images/image.jpg
firstSeen: 2023-02-11T20:00:00-04:00
---

Optimize the performance of a component by using a value that is slightly out of date, rather than re-rendering immediately with the latest value. Use this when an element has low priority and doesn't require up-to-date value.

- use the `useState()` hook to create a state that holds the up-to-date data.
- use the `useDeferredValue()` hook to create a variable for holding the slightly outdated state, initialize it with the value of the `state`.

```jsx
function Counter() {
	const [count, setCount] = React.useState(0);
	const deferredCount = React.useDeferredValue(count);

	return (
		<>
			<button onClick={() => setCount(count + 1)}>Increment</button>
			<p>Count: {deferredCount}</p>
		</>
	);
}
```

```jsx
ReactDOM.render(<useCounter />, document.getElementById('root'));
```
