# JQuery/Ajax Quiz

Write your answer below each question. 

### Question 1
(a) What is a click handler? 

  A click handler is a JQuery command that assigns a listener to an HTML button. It listens for the button to be clicked and then executes the specified function.

(b) Where in your JS file should you put it, and WHY? 

  Click handlers should be in the document ready statement otherwise the HTML page may not be ready and the button may not exist when the JS file attempts to assign the click handler to the button resulting in a button that doesn't do anything.

### Question 2
If you get the error `$ is undefined`, what does that mean and what could you do to fix it?

  This probably means that the JQuery library has not been linked to in the HTML script. Link the JQuery library before linking the JS file.

### Question 3
What should go in the `$(document).ready()` part of your JS file? 

  Anything that will be assigning events to HTML elements, or any initial AJAX requests that need to be run. These can all be placed in an initialization function that is declared outside of the doc ready and then called within it.

### Question 4
In an AJAX GET request, what does the argument of the `.done()` callback - in the example below, that would be `data` - represent? 

  the argument of the .done() callback in a GET request is the variable to which all the data that you retrieved is assigned. Below the data represents all of the users JSON data from the hacker news API.

```
$.ajax({
    url: 'http://ig-hacker-news.herokuapp.com/users',
    type: 'GET',
  })
  .done(function(data) {
    console.log("success!")
  });
```
### Question 5
In an AJAX POST request, what does the argument of the `.done()` callback - in the example below, that would be `data` - represent? (Hint: it's not the same as in Question 4.)
  
  the argument of the .done() callback in a POST request is the variable to which the new posted data is assigned. The data below would be the JSON for all the data for the new user Anna.

```
  $.ajax({
    url: 'http://ig-hacker-news.herokuapp.com/users',
    type: 'POST',
    dataType: 'JSON',
    data: { user: { name: "Anna", about: "instructor", email: "hi@gmail.com" } },
  })
  .done(function(data) {
    console.log("success!");
  });
```
### Question 6
Suppose you had the following form in your HTML file. Use jQuery to write a single line of code that takes whatever the user entered in the textbox and saves it to the variable `user_input`. 

var $dresscolor = $('#color').val();

```
  <form>
    <p>The dress is:</p><input type="text" id="color">
    <input type="submit" value="Submit" id="submit">
  </form>
```

### Question 7
This code looks like it works, but when you run it, you see that the `UserApp.add_all_users()` function executes but `console.log` displays `undefined`. What's wrong with the code? 

  The UserApp.add_all_users(data); call is outside of the scope of the AJAX .done() callback. If you move the call to the function within the done callback than data will be defined and the code will work.

```
UserApp.get_all_users = function() {
  $.ajax({
    url: 'http://ig-hacker-news.herokuapp.com/users',
    type: 'GET',
  })
  .done(function(data) {
    console.log("success!")
  });
  UserApp.add_all_users(data);
};

UserApp.add_all_users = function(data) {
  console.log(data);
};
```



