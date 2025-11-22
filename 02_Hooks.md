# # React Js

# # Event Handling in React

- Event handling in React enables components to respond to user interactions, such as clicks, key presses, or form submissions.
- React events are written in camelCase
- **Syntax** :- `<element onEvent={handlerFunction} />`
  - **element** : The JSX element where the event is triggered (e.g., <button>, <input>, etc.).
  - **onEvent** : The event name in camelCase (e.g., onClick, onChange).
  - **handlerFunction** : The function that handles the event when it occurs.
 
### Example :-

On clicking button in browser in console message shows "Button Clicked"

```jsx
import React from "react";
import Card from "./Card";

const ProductItem = (props) => {

// Function for Event 
	function clickHandler() {
		console.log("Button Clicked");
	}

	return (
		<Card className="product-item">
{/* Event Listener */}
			<button onClick={clickHandler}>Add to Cart</button>
		</Card>
	);
};

export default ProductItem;
``` 

# # UseState Hook

- It is a Hook that enables functional components to manage and update state.
- It allows you to add stateful behavior to functional components without needing to convert them into class components.
- **Syntax** :-  `const [state, setState] = useState(initialState)`
  - **state** : It is the value of the current state.
  - **setState** : It is the function that is used to update the state.
  - **initialState** : It is the initial value of the state.

> [!NOTE]
> Per Compinent instance basics.  
> Each component is running separately.

### Example :-

- On clicking button UI will change .
- Title cahnged by "Popcorn"

```jsx
import React, {useState} from "react";
import Card from "./Card";

const ProductItem = (props) => {

	// UseState for Title
	const [title, setTitle] = useState(props.title);

	// Function for Event Handling 
	function clickHandler() {
		// Changing Title
		setTitle("Popcorn");
		console.log("Button Clicked");
	}

	return (
		<Card className="product-item">
			<div className='product-item__description'>
				{/* Title Name */}
				<h2>{title}</h2>
			</div>
			{/* Event Listener*/}
			<button onClick={clickHandler}>Add to Cart</button>
		</Card>
	);
};

export default ProductItem;
```

# # UseEffect Hook

- It is used to handle side effects in functional components.
- Side Effects are :
  - Fetching data from an API.
  - Setting up event listeners or subscriptions.
  - Manipulating the DOM directly (although React generally handles DOM manipulation for you).
  - Cleaning up resources when a component unmounts
- **Syntax** :-

``` js
useEffect(() => {
    // Code to run on each render
    return () => {
        // Cleanup function (optional)
    };
}, [dependencies]);
```

### Example :-

- UI will be rendered when the user enters OR update any text in input box.
- 3 Variation are When Ui renders
  - Run on Every Render
  - Run on First Render
  - First Render + Whever dependency changes
- 4th Variation is Cleanup Function --> 

``` js
import { useEffect, useState } from "react";
import "./App.css";

function App() {
  const [text, setText] = useState("");
  const [name, setName] = useState("Abhishek");

  // Variation 1 --> Run on Every Render

  // useEffect(()=>{
  //   console.log("UI Rendering Done");
  // })

  // Vriation 2 --> Run on First Render

  // useEffect(() => {
  //   console.log("UI Rendering Done");
  // },[]);

  // Variation 3 --> First Render + Whever dependency changes

  // useEffect(() => {
  //   console.log("Change Observed");
  // }, [name]);


  // Variation 4 --> To handle unmounting of a component

  useEffect(() => {
    console.log("Listener Added");              // This line will run second              

    return () => {                              // Cleanup Function
      console.log("Listener Removed");          // This line will run first
    };
  }, [text]);


  function changeHandler(event) {
    setText(event.target.value);
    console.log(text);
  }

  return (
    <div className="App">
      <input className="btn" type="text" onChange={changeHandler}></input>
    </div>
  );
}

export default App;
```














































