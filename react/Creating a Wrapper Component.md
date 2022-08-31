# Creating a Wrapper Component

We can wrap our components to return multiple root level tags. We can't return multiple without wrapping because JSX does not allow us to do so.

```
const Wrapper = props => {
	return props.children;
}

export default Wrapper;
```

And we can use this wrapper in some other JSX files.

```
import Wrapper from '../Wrapper';

const Element = (props) =>{

	return (
		<Wrapper>
			<div></div>
			<p></p>
		</Wrapper>
	)

}
```