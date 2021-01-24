# Fetch API

## What is an API?

An API is the way applications speak to each other.

API calls follow a *request/response* pattern. We request information and we receive that information as a response. Every time we open a browser, or go to a website we are making a request to a server and what we see is the response from the server.

<hr>

## Fetch API

The Fetch is a way used to make *requests*, such as calling an API or fetching a remote resource or HTML file from a server.


### Let’s look at how it works:

the fetch() takes a url:

Let’s say you wanted to get a list of repositories from the GitHub API for a specific user

```js
fetch('https://api.github.com/users/sara219/repos')
```

The first part `(https://api.github.com)` - *domain name* - is like the address of a block of flats. The second part `(users/sara219/repos)` is what we call an *endpoint*; this specifies a specific flat. 
The fetch function goes to the address that we give it and asks for information at that address.


The fetch() method returns a Promise. We handle API responses using `then()` and `catch()`. 

Let’s log the response to the console.

```js
fetch('https://api.github.com/users/sara219/repos')
  .then(response => {
    // here we're turning the response into JSON.
    return response.json();
  })
  .then(data => {
    // Here's a list of repos!
    console.log('success!', data);
  })
  .catch(error => {
      // There was an error
    console.log('Something went wrong', error);
  });

```

**NOTE**: By default the Fetch API uses the *GET* method -> GET all the repos for that user! 

**Fetch API Methods**
 * **GET**: gets resources such as HTML, JS, CSS.
 * **POST**: sends data to a server in the body of the request.
 * **PUT**: creating or updating data
 * **DELETE**: deletes data.