Hello HTTP
======

Use the Node.js `http` module to create an http server. 

## Directions

Your server should:
1. Respond with a greeting if the method is `GET` and url (path) is `/greeting/<name>`
  * If query string specifies a `salutation` like `/greeting/jane?salutation=yo`, use that
    for the greeting salutation, otherwise `hello`
  * If name is not included, use `stranger`, otherwise use name in greeting
2. Responds with one random of (at least) three interesting facts about http (up to you) when method is 
GET and the url (path) is `/fact`. **Return the fact as an object with a fact property and make sure Content-Type 
is `application/json`**. (Make sure that each interesting fact as the word `http` somewhere in the fact, 
this will make it easier to test the fact.)
3. **BONUS** Add more routes! Consider:
    1. Path (url)
    1. Query
    1. Method (though we won't read body unitl t
4. Any other request that doesn't match a defined `METHOD` and url `path` should return status code 404 Not Found 
and include the text: `CANNOT <METHOD> <path>`

**IMPORTANT**: Add a `README.md` that describes how to use your API 

### Architecture and Design

1. Define the listening function for your server in `lib/app.js`, but export it and create the server and listen 
in a `server.js` file at the root of your project. You will import (`require`) this same function into your E2E test
and use `chai.request(app)` to start the server
* Use 'extract' function to not have all of your code live in the listening function. You should be able to do this
for 1) greeting, 2) interesting fact, 3) other BONUS methods. TDD these synchronous functions first before 
exposing via the server.

## Testing
* Unit test your discrete module functions for making a greeting and returning an interesting fact. For the 
randomly returned interesting fact, just test the word http as a regex:

    ```js
    assert.ok(/http/.test(response));
    ```

* Use chai-http to E2E test the API.
