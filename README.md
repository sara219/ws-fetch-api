# Fetch API

## What is an API?

API stands for application programming interface, which is a software intermediary that allows two applications to talk to each other. Each time you use an app like Facebook, send an instant message, or check the weather on your phone, you're using an API.

![api](https://hackernoon.com/hn-images/1*CkynRe-J1FVnUAk7JmOTdQ.gif)


API calls follow a *request/response* pattern. We request information and we receive that information as a response. Every time we open a browser, or go to a website we are making a request to a server and what we see is the response from the server.

<hr>

## Fetch API

The Fetch is a way used to make *requests*, such as calling an API or fetching a remote resource or HTML file from a server.


### Let’s look at how it works:


Let’s say you wanted to get a list of repositories from the GitHub API for a specific user, the fetch() takes the API:

```js
fetch('https://api.github.com/users/sara219/repos')
```

The first part `(https://api.github.com)` - *domain name* - is like the address of a block of flats. The second part `(users/sara219/repos)` is what we call an *endpoint*; this specifies a specific flat. 
The fetch function goes to the address that we give it and asks for information at that address.


The fetch() method returns a Promise. We handle API responses using `then()` and `catch()`. 

> Let’s log the response to the console.

```js
fetch('https://api.github.com/users/sara219/repos')
  .then(response => console.log(response)) 
  // The API call was successful!
  .catch(error => console.log('Something went wrong', error))
  // There was an error

```
> Look at the object that comes back. 

**Notice:**
* `Response.body`: the readable stream of the response's body.
* `Response.headers`: HTTP headers allow the client and the server to pass additional information with the request or the response. An example are *status codes*.

As we said the response.body isn’t usable JSON. It’s something called a ReadableStream. To get our API data as a JSON object, we can use a method native to the Fetch API: ***json()***

```js
fetch('https://api.github.com/users/sara219/repos')
  .then(response => {
    return response.json();
    // here we're turning the response into JSON
  })
  .then(data => {
    console.log(data);
     // Here's a list of repos!
  })
  .catch(error => {
    console.log(error);
  });
```
> *check the console now!*

**NOTE:** By default the Fetch API uses the GET method, there are different methods:

* **GET**: retrieve data from the server.
* **POST**: Sends data to the server and creates a new resource
* **PUT** : Update an existing resource (overwriting)
* **DELETE**: deletes data.

