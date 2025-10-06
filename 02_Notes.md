# # React Js

# # Event Handling in React

- Event handling in React enables components to respond to user interactions, such as clicks, key presses, or form submissions.
- React events are written in camelCase
- **Syntax** :- `<element onEvent={handlerFunction} />`
  - **element** : The JSX element where the event is triggered (e.g., <button>, <input>, etc.).
  - **onEvent** : The event name in camelCase (e.g., onClick, onChange).
  - **handlerFunction** : The function that handles the event when it occurs.
 
### Example :-

On clicking button in browser console message shows "Button Clicked"

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
