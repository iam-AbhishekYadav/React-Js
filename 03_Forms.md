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
                ...prevFormData,
                [event.target.name]: event.target.value
            }
        });
    }

    return (
        <div className="App">
            <form onSubmit={submitHandler}>

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
                ...prevFormData,
                [event.target.name]: event.target.value
            }
        });
    }

    return (
        <div className="App">
            <form onSubmit={submitHandler}>

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

# # Checkboxes, Radio Button and Select in Form


``` js

``` js
import React from 'react';
import { useState } from 'react';

function App() {

    const [formData, setFormData] = useState({
        isVisible: true,
        mode: "",
        favCar: ""
    });

console.log(formData);  // To see the form data in the console

    function changeHandler(event) {
        const { name, type, value, checked } = event.target;
        setFormData((prevFormData) => {
            // console.log(prevFormData);
            return {
                ...prevFormData,
                [name]: type === 'checkbox' ? checked : value
            }
        });
    }

    function submitHandler(event) {
        event.preventDefault();
        // Do something with the form data
        console.log("Form Submitted");
        console.log(formData);
    }

    return (
        <div className="App">
            <form onSubmit={submitHandler}>

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
                        checked={formData.mode === "Online Mode"}
                    ></input>

                    <label htmlFor='Online-mode'>Online Mode</label>


                    <input
                        type='radio'
                        onChange={changeHandler}
                        name='mode'
                        value="Offline Mode"
                        id='Offline-Mode'
                        checked={formData.mode === "Offline Mode"}
                    ></input>

                    <label htmlFor='Offline-mode'>Offline Mode</label>

                </fieldset>

                <br />
                <br />

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


                <br /> */}


                {/* First way to create submit button */}
                {/* <input
                    className="m-4 p-2 bg-blue-500 text-white rounded-lg"
                    type="submit"
                    value="Submit"
                ></input> */}

                {/* Second way to create submit button */}

                <button
                    className="m-4 p-2 outline-2 bg-gray-300 rounded-lg hover:bg-gray-400"
                    type="submit"
                >Submit</button>

            </form>
        </div>
    );
};

export default App;
```































































































