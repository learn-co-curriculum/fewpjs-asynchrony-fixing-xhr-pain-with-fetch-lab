# Fixing XHR Complications with Fetch

## Learning Goals

- Update and Refactor Asynchronous Code
- Practice utilizing fetch in place of `XMLHttpRequest`s

## Introduction

In the previous lesson, we briefly explored how `XMLHttpRequest`s can be required to
do a bit of code nesting. When building web apps and pages, this sort of thing
can happen a lot. Imagine you wanted to build an app that checked the weather,
then, depending on the received data, checked for weather-appropriate local
events. One request for data is dependent on the other, requiring us to wait
for the resolution of the first request before sending the next.

With `XMLHttpRequest`s, programmers are required to write the code for opening,
setting up, then sending requests, adding complication to the process.

In this lab, we're going go back to using [fetch][], tackling the same problem
from the previous lab, but with cleaner, easier to understand code.

## JSON Server

As with the previous lab, this lab uses [json-server][]. JSON Server allows us
to spin up a fake RESTful API. After running `npm install` or `learn` for the
first time, to start up JSON Server, run `json-server --watch db.json` in your
console. Once the server is running, you'll see a list of available resource
paths:

```bash
Resources
  http://localhost:3000/posts
  http://localhost:3000/comments
```

These endpoints each provide a different set of data. Since it is mimicking a
RESTful API, sending a request to 'http://localhost:3000/posts' will return all
forum posts, while 'http://localhost:3000/posts/1' will return the forum post
with the id of 1.

The tests do not need JSON Server to be running, but if you would like to run
tests while also running the server, open a second tab in your terminal.

## Instructions

Working code is already provided in `index.js`, but it currently implements
`XMLHttpRequest`s. Your task is to replace the existing XHR code with its fetch
equivalent. Get all of the content rendering again using fetch in order to
pass the tests.

**Note:** Unlike `XMLHttpRequest`s, when a `fetch()` request is completed, it returns
a [Response][] object. Because `fetch()` returns a [Promise][], we can access this
Response object using `.then()`. We'll be digging into `Promise` in the next few lessons.
Check out the [Using Fetch][] documentation for examples. 

## Conclusion

In regard to how we use it, `fetch()` is similar enough to `XMLHttpRequest`s that we
can actually swap between them without requiring a lot of modifications to our
code. With `fetch()`, however, we can achieve the same results with less code. In
addition, `fetch()` provides additional features (like handling scenarios where one
request, upon which another requests depends, fails).

The key to what makes `fetch()` so clean is the `Promise` class. `Promise`s can be used
in many places but networking is a very natural starting point. Since `Promise` was introduced
to JavaScript engines it has proliferated greatly. Let's see how `Promise` makes `fetch()` so
smooth!

## Resources

- [Using Fetch][]
- [Promises][promise]
- [Response][]

[using fetch]: https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch
[fetch]: https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API
[promise]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise
[response]: https://developer.mozilla.org/en-US/docs/Web/API/Response
[json-server]: https://github.com/typicode/json-server
