# Use Reducer

```
const [emailState, dispatchEmail] = useReducer();
```

useReducer takes an anonymous function for the first input.
```
const [emailState, dispatchEmail] = useReducer(emailReducer);
```

We can initialize our state as second input in this useReducer function.

```
const [emailState, dispatchEmail] = useReducer(emailReducer, {
	value: '',
	isValid: false,
});
```

We can write it seperatly to easy read purposes.


This anonymous function should get a state snapshot and an action was dispatched for inputs. This function must return new state.

```
const emailReducer = (state, action) =>{
	return{value: '', isValid: false}
};
```

We can use our emailState as a variable in react code. Like this:

```
let variableExample = emailState.value;
let variableExample2 = emailState.isValid;
```

We should dispatch actions to change its value.
```
dispatchEmail({type: 'USER_INPUT', val: event.target.value});
 ```
 
 Now we can modernize our reducer to fit action types.
 
 ```
const emailReducer = (state, action) =>{

	if(action.type === 'USER_INPUT'){
		return{value: action.val, isValid: action.val.includes('@') };
	}
	
	if(action.type === 'INPUT_BLUR') {
		return { value: state.value , isValid: state.isValid };
	}
	
	return{value: '', isValid: false}
};
```