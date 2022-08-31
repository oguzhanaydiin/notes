# Create Mui Theme

```
import { createMuiTheme, ThemeProvider } from '@material-ui/core'
import { purple } from '@material-ui/core/colors'
```

This function takes an object as an argument. This object represent the team we wanted to create. We can pick and choose which properties we want to override. 

```
const theme = createMuiTheme({
	palette: {
		primary: {
			main: '#fefefe'	
		},
		secondary: purple
	},
	typography: {
		fontFamily: 'Quicksand',
		fontWeightLight: 400,
		fontWeightRegular: 500,
		fontWeightMedium: 600,
		fontWeightBold: 700,
	}
})
```

After created theme, we need to provide the theme to function. We just need to wrap everything with ThemeProvider component

```
function App(){
	return(
		<ThemeProvider theme={theme}>
			<Route exact path="/">
				<Notes/>
			</Route>
		</ThemeProvider>
	);
}
```