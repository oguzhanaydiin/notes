# React Portals

In the terms of writing cleaner html and seeing a cleaner DOM, we should not use nested overlay contents, its not a good structure. It'll work either way but using portals for this kind of situation is better.

Portal need two things. You need a place to port the component to and let you know the component that it should have a portal to that place.

Go into index.html, create a div with id.

```
<div id="backdrop-root"></div>
<div id="overlay-root"></div>
```
Then you will go to the JSX file that you wanted to be portaled.
You should insert createPortal function with two inputs. First react node that should rendered (it wants JSX so give it a tag input). Second input is a pointer to the realDOM where this element should rendered in.
```
import ReactDOM from 'react-dom';

const Backdrop  = (props) => {
	return <div className={classes.backdrop} onClick={props.onConfirm} />
};

const Backdrop  = props => {
	return <Card className={classes.modal}>
		<header>
		</header>
		<footer>
		</footer>
	</Card>
};

const ErrorModal = (props) => {
	return (
		<>
			{ReactDom.createPortal(
				<Backdrop onConfirm={props.onConfirm} />, 
				document.getElementById('backdrop-root')
			)}
		</>
	);
}

export const ErrorModal;
```