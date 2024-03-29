# Create a New React App:

```
npx create-react-app my-app
cd my-app
npm start
```

## For personalization i generally delete src folder. After deleting src folder deleting all items except "index.html", "manifest.json" and "robots.txt" inside public folder.

## Personalization guide after deleting those folders:

* 1 - Create src folder.
* 2 - Create "index.js" file inside src folder and write down code below:

import React from 'react';
import ReactDOM from 'react-dom';

import App from './App';

ReactDOM.render (<App />, document.getElementById('root'));

* 3 - Create App.js file inside src folder and create a generic App function (rafce command should help):

```
import React from 'react'

const App = () => {
  return (
    <div>App</div>
  )
}

export default App;
```

## Finally
Now you can "npm start" the application.

# Adding React-Bootstrap:

* 1 - "npm install react-bootstrap bootstrap"
* 2 - Add the "import 'bootstrap/dist/css/bootstrap.css';" line to index.js file

Now you can import any bootstrap component and use in any function.

Example: 
import Button from 'react-bootstrap/Button';

```
export default function ButtonExample() {
  return (
    <>
      <p>
        <Button variant="primary">
          Primary Button
        </Button>
      </p>
    </>
  );
}
```

