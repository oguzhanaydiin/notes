# Make Styles Hook

```
import { makeStyles } from '@material-ui/core'
```

We can write styles with *camel case*. Its important that must be written in camel case.

```
const useStyles = makeStyles ({
	btn: {
		fontSize: 60,
		backgroundColor: 'violet',

		'&:hover': {
			backgroundColor: 'blue'
		}
	},
	title:{
		textDecoration: 'underline',
		marginBottom: 20
	}
})
```

This function gives us a hook. Then we use this hook in function to get the classes. Then we can use functions for appearences.

```
export default function Create() {

	const classes = useStyles();

	return(
		<Container>
			<Button
				className={classes.btn}
				onClick={()=> {} }
				type="submit"
				variant="contained"
			
			>
				Create a New Note
			</Button>
		</Container>
	
	);


}
```