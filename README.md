# ReactForm-Input
1.Open up FoodOrderForm.js. We’ll start laying down the foundation of our form.

Inside the FoodOrderForm component’s return statement, add a <form> element.

2.
Inside the <form></form> tags, create an <input> field each for name, phone, address, and order.

For each <input>, add an id attribute set to the information it is responsible for, such as "name", "phone", "address", and "order".

3.
Attach a <label> element to each <input> element.

Each label should have the attribute htmlFor with a string value of the corresponding <input> element’s id. This will associate the <label> with its respective <input> element and improve accessibility for users.

4.
Great, the foundation is taking shape!

Let’s now add a button at the bottom of our form. You can set the text of the button to "Submit Order" and include a type attribute with a value of "submit". This will let the browser know that this button is intended to submit the form.

Controlling the Form
5.
Currently, our form is uncontrolled. It does not use React to control its state and update the values of the input field.

We need to change that and hand the control to React. Take a moment to consider what form data you should be storing and how a State Hook can help you with that.

Since our form keeps track of information like name, phone, address, and order, let’s create a state for each piece of information.

Inside the FoodOrderForm component and above the return statement, use the State Hook to define a state variable for each piece of information, along with their state setters.

Initialize all state variables to an empty string.

6.
Now that we have the state variables set up, we can make some modifications to our <input> elements.

For each <input> element, add a value attribute and set the value to the corresponding state variable.

7.
Wonderful. React now has control over the form!

This form still needs to update the input field and state variables when the user types. To do this, you need to use the onChange event listener to listen for changes.

Update each <input> element by giving it an onChange event handler.

Start with the name input. Inside the onChange event handler, give it this callback function.

onChange={(e) => setName(e.target.value)}

This calls the corresponding state setter function setName and passes in the new value of the input field retrieved from the event object.

This will update the state of the corresponding state variable with the new value entered by the user.

8.
Repeat the same for the remaining <input> elements, just as you did with the name input field.

Give each <input> element an onChange event handler and pass in a callback function that updates the corresponding state variable of each input based on the values of e.target.value.

Form Submission
9.
Congrats! Your form now updates the state variable live as the user types, and the page re-renders to reflect that.

You need to now handle the submission of the form.

Inside the FoodOrderForm component, define a handleSubmit() function to manage the submitted form data. The function should receive an event object, e, in its parameter.

In the function body, prevent the form from taking its default action with e.preventDefault(). Rather than using the default action, we want to have it alert the user instead.

10.
While still in the function body of handleSubmit(), alert the user using the JavaScript function alert().

The alert should output the user’s order data in this format.

Order Successful!

Your order was <user's orders>.

Please show your confirmation number for pickup.

11.
Pass the handleSubmit() function to the form by giving the form tag an onSubmit event listener with the value handleSubmit.

12.
Wonderful! The form is working quite well already.

Let’s clean up a little and add some necessary information before submitting it to Saucy Tango for use.

Complete each <input> element by giving each a name attribute and a type attribute, specifying the appropriate name and type for each input.
# solution 

```jsx
import React, { useState } from "react";

function FoodOrderForm() {
  // Define state variables
  const [name, setName] = useState('');
  const [phone, setPhone] = useState('');
  const [address, setAddress] = useState('');
  const [order, setOrder] = useState('');

  // Define handleSubmit function
  const handleSubmit = (event) => {
    event.preventDefault(); // Prevent default form submission
    alert(`Order Successful!\n\nYour order:\nName: ${name}\nPhone: ${phone}\nAddress: ${address}\nOrder: ${order}\n\nPlease show your confirmation number for pickup.`); // Alert user
  };

  return (
    <form onSubmit={handleSubmit}>
      {/* Add input fields and labels */}
      <div>
        <label htmlFor="name">Name:</label>
        <input type="text" id="name" name="name" value={name} onChange={(e) => setName(e.target.value)} />
      </div>
      <div>
        <label htmlFor="phone">Phone:</label>
        <input type="text" id="phone" name="phone" value={phone} onChange={(e) => setPhone(e.target.value)} />
      </div>
      <div>
        <label htmlFor="address">Address:</label>
        <input type="text" id="address" name="address" value={address} onChange={(e) => setAddress(e.target.value)} />
      </div>
      <div>
        <label htmlFor="order">Order:</label>
        <input type="text" id="order" name="order" value={order} onChange={(e) => setOrder(e.target.value)} />
      </div>
      {/* Add submit button */}
      <button type="submit">Submit Order</button>
    </form>
  );
}

export default FoodOrderForm;

```
# -----------------------------------------Project 2  ---------------------------------
# solution https://codepen.io/nickefr-the-flexboxer/pen/qBGBaKr
