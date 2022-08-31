# Handling Side Effects with the useEffect Hook

Use Effect hook is a utility hook that you can render some of your function in conditional states. Ex: creation of the page.

```
useEffect(() => { ... }, [ dependencies ] );
```

First side of this function, is a function that should be executed AFTER every component evaluation IF the specified dependencies changed at the second part of the hook.

Example usage of this hook:

```
useEffect(() => { 
	const storedData = localStorage.getItem('isLoggedIn');

	if(storedData === '1)[
		setIsLogg	
	}

}, [  ] );
```

If the dependencies are empty, useEffect will execute when the function first run.

```
useEffect(() => { 
	const identifier = setTimeout(()=> {
		doCode();
	}, 500);

	return () => {
		clearTimeout(identifier);
	};

}, [ enteredPassword ] );
```

return in useEffect works BEFORE useEffect executes (unless its the first execution of the page.)