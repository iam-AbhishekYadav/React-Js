# # Forms in React

- Forms are used to take input from users, like text, numbers, or selections.

### Example :-

- Two inputs for First Name and Last Name
- Both inputs are handled by one handler

``` js
import React from 'react';
import { useState } from 'react';


function App() {

const [formData, setFormData] = useState({
        firstName: "",
        lastName: "",
    });

    console.log(formData);  // To see the form data in the console


    function changeHandler(event) {
        setFormData((prevFormData) => {
            // console.log(prevFormData);
            return {
                ...prevFormData,        // Spreading the previous form data
                [event.target.name]: event.target.value
            }
        });
    }

    return (
        <div className="App">
            <form>

                <input
                    type="text"
                    placeholder="First Name"
                    onChange={changeHandler}
                    name="firstName"
                ></input>

                <br/>

                <input
                    type="text"
                    placeholder="Last Name"
                    onChange={changeHandler}
                    name="lastName"
                ></input>

            </form>
        </div>
    );
};


export default App;
```

# # Conrolled Components

- The form elements managed by React state, allowing React to control and update their values for better input handling and validation.
- This makes it easier to debug and keeps data consistent throughout the app.

## Flow of Controlled Components

- **`Input Element`** : The user changes the input value.
- **`Change Handler`** : The onChange event captures the new value and updates the state.
- **`Component State`** : The state holds the updated input value.
- **`Validate & Update`** : The value is validated and the state is updated.
- **`Re-render`** : The input element is re-rendered with the updated value.

<img src="https://github.com/user-attachments/assets/7d9acbb8-d55e-4931-95a1-4382d4292953" width="700" height="600">


### Example :-

``` js
import React from 'react';
import { useState } from 'react';


function App() {

const [formData, setFormData] = useState({
        firstName: "",
        lastName: "",
    });

    console.log(formData);  // To see the form data in the console


    function changeHandler(event) {
        setFormData((prevFormData) => {
            // console.log(prevFormData);
            return {
                ...prevFormData,        // Spreading the previous form data
                [event.target.name]: event.target.value
            }
        });
    }

    return (
        <div className="App">
            <form>

                <input
                    type="text"
                    placeholder="First Name"
                    onChange={changeHandler}
                    name="firstName"
                    value={formData.firstName}
                ></input>

                <br/>

                <input
                    type="text"
                    placeholder="Last Name"
                    onChange={changeHandler}
                    name="lastName"
                    value={formData.lastName}
                ></input>

            </form>
        </div>
    );
};


export default App;
```

# # Checkboxes and Radio Button in Form

- In Checkboxes and Radio Button we use `checked` insted of value.
- The value will be obtained by doing destructuring
``` js

``` js
import React from 'react';
import { useState } from 'react';

function App() {

    const [formData, setFormData] = useState({
        isVisible: true,
        mode: "",
    });

console.log(formData);        // To see the form data in the console

    function changeHandler(event) {
        const { name, type, value, checked } = event.target;        // Destructring
        setFormData((prevFormData) => {
            // console.log(prevFormData);
            return {
                ...prevFormData,        // Spreading the previous form data
                [name]: type === 'checkbox' ? checked : value        // Handling checkbox separately
            }
        });
    }

    return (
        <div className="App">
            <form>

                <input
                    type='checkbox'
                    onChange={changeHandler}
                    name='isVisible'
                    id='isVisible'
                    checked={formData.isVisible}
                ></input>

                <label htmlFor='isVisible'>Am I Visible ?</label>

                <br />
                <br />

                <fieldset>
                    <legend>Mode Selection</legend>

                    <input
                        type='radio'
                        onChange={changeHandler}
                        name='mode'
                        value="Online Mode"
                        id='Online-Mode'
                        checked={formData.mode === "Online Mode"}        // Checking which radio is selected
                    ></input>

                    <label htmlFor='Online-mode'>Online Mode</label>


                    <input
                        type='radio'
                        onChange={changeHandler}
                        name='mode'
                        value="Offline Mode"
                        id='Offline-Mode'
                        checked={formData.mode === "Offline Mode"}        // Checking which radio is selected
                    ></input>

                    <label htmlFor='Offline-mode'>Offline Mode</label>

                </fieldset>

            </form>
        </div>
    );
};

export default App;
```



# # Text Area, Dropdown/Select and Submit Button in Form



``` js
import React from 'react';
import { useState } from 'react';


function App() {

const [formData, setFormData] = useState({
        comments : "",
        mode: "",
    });

    console.log(formData);  // To see the form data in the console


    function changeHandler(event) {
        setFormData((prevFormData) => {
            // console.log(prevFormData);
            return {
                ...prevFormData,        // Spreading the previous form data
                [event.target.name]: event.target.value
            }
        });
    }

  function submitHandler(event){        // To prevent default behaviour of form submission
    event.preventDefault();
    // Do something with the form data
    console.log("Form Submitted");
    console.log(formData);
  }

  return (
    <div className="App">
      <form onSubmit={submitHandler}>

        <textarea
          placeholder='Enter your comments here ...'
          onChange={changeHandler}
          name='comments'
          value={formData.comments}
        ></textarea>


        <br/>


        <label htmlFor='favCar'> Select your favorite car</label>

        <select
          name='favCar'
          id='favCar'
          value={formData.favCar}
          onChange={changeHandler}
        >
          <option value="">-- Choose your favorite car --</option>
          <option value="BMW">BMW</option>
          <option value="Audi">Audi</option>
          <option value="Mercedes">Mercedes</option>
          <option value="Tesla">Tesla</option>
        </select>


        <br/>


        {/* First way to create submit button */}

        {/* <input
          type="submit"
          value="Submit"
        ></input> */}

        {/* Second way to create submit button */}

        <button 
          type="submit"
        >Submit</button>

      </form>
    </div>
  );
};

export default App;
```



























































































