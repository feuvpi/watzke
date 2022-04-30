---
title: Using the Axios dependency to send promise-based HTTP requests.
date: "2022-03-06T22:40:32.169Z"
description: "Using the Axios dependency to interact with external APIs."
---
<div style="text-align: justify">

##### Sending an HTTP request to an external API using Axios.

###### ABOUT AXIOS

Axios is a promise-based HTTP client for Node.js. This open-source tool can be used to handle external API communications objectvily. 

###### INSTALLING AXIOS IN THE PROJECT

There are two main ways to install Axios in our project:

- `npm:`

```
$ npm install axios // highlight-line
```

- `yarn:`

```js
$ yarn add axios

```

- `bower:`

```js
$ bower install axios

```

- `contend delivery network:`

```js
$ <script src="https://unpkg.com/axios/dist/axios.min.js"></script>

```


###### USING ASYNCHRONOUS FUNCTIONS WITH AXIOS TO PERFORM EXTERNAL REQUESTS

With Axios we can make HTTP requests using `GET`, `POST`, `PUT`, `DELETE`, `PATCH`, `OPTIONS` and `HEAD` methods. One of the ways to achieve this is with asynchronous functions. To practice it, we are going to send a request for the upcoming movies in the  [TheMovieDB`s API](https://www.themoviedb.org/documentation/api) using `async/await` method. 

```js
const axios = require('axios');
const BASE_URL = 'https://api.themoviedb.org/3/';
const buildURL = path => `${BASE_URL}${path}?api_key=${API_KEY}`


 async function callAPI() {
    const path = "movie/upcoming"
    const call = await axios.get(buildURL(path))
    console.log(call.data.results)
}
 
console.log(callAPI())
```
As a result, we receive a JSON format list where each object represents a movie that will be released soon:

```Promise { <pending> }
[
  {
    adult: false,
    backdrop_path: '/yuvFyfOAO2UB5YP0HKgu8imtJul.jpg',
    genre_ids: [ 28, 12 ],
    id: 335787,
    original_language: 'en',
    original_title: 'Uncharted',
    overview: 'A young street-smart, Nathan Drake and his wisecracking partner Victor “Sully” Sullivan embark on a dangerous pursuit of “the greatest treasure never found” while also tracking clues that may lead to Nathan’s long-lost brother.',
    popularity: 1029.461,
    poster_path: '/tlZpSxYuBRoVJBOpUrPdQe9FmFq.jpg',
    release_date: '2022-02-10',
    title: 'Uncharted',
    video: false,
    vote_average: 7.5,
    vote_count: 135
  }, [...]
  
  ```
In that way, Axios can be used in projects to handle HTTP requests and API communication. 

<div style="text-align: right">

###### []'s 
