# Material Ui Text Fields

```
function App(){
	const classes= useStyles()
	const [title, setTitle] = useState('')
	const [titleError, setTitleError] = useState(false)


	const handleSubmit = (e) => {
		//means dont refresh page
		e.preventDefault();
		setTitleError(false)

		if(title == '') {
			setTitleError(true)
		}
		
		if(title && details) {
			console.log(title, details)
		}
	}

	return (
		<Container>
			<form noValidate autoComplete="off" onSubmit={handleSubmit}>
				<TextField 
					label="Note Title"
					variant="outlined"
					color="secondary"
					fullWidth
					required
					onChanged={(e)=> setTitle(e.target.value)}
					error={true}
				/>
			</form>
		</Container>
	)

}
```

noValidate means we dont want to use built-in validation messages, we wanna handle ourselfs.