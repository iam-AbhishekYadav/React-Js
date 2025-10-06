# # React Js

# # Event Handling in React

- Event handling in React enables components to respond to user interactions, such as clicks, key presses, or form submissions.
- React events are written in camelCase
- **Syntax** :- `<element onEvent={handlerFunction} />`
  - **element** : The JSX element where the event is triggered (e.g., <button>, <input>, etc.).
  - **onEvent** : The event name in camelCase (e.g., onClick, onChange).
  - **handlerFunction** : The function that handles the event when it occurs.
 
### Example :-

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
