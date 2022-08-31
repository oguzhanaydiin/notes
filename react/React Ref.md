# React Ref

Ref is a hook that returns a reference in DOM to use later. You can connect any of your html elements to one of your refs. You most likely to use in input elements though.

```
const nameInputRef = useRef();

<input
	id="username"
	ref={nameInputRef}

/>
```
Now you can connect with your HTML element's DOM node and get his current value and reading data.