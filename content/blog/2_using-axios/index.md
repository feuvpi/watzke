---
title: Utilizando a dependência Axios para realizar requisições HTTP promise-based.
date: "2022-03-06T22:40:32.169Z"
description: "Utilizando a dependência Axios para comunicação com API's externas."
---
<div style="text-align: justify">

##### Vamos realizar uma requisição HTTP para uma API externa utilizando o modulo Axios. 

###### Sobre o Axios

O Axios é um cliente HTTP promise-based para o node.js e para o browser. Utilizando essa ferramenta open-source é possível realizar requisições HTTP em APIs externas de forma simples e objetiva.

###### Instalando o Axios no Projeto

Podemos instalar o Axios das seguintes formas:

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


###### Utilizando funções assíncronas com axios para realizar solicitações externas

Com o Axios conseguimos realizar requisições HTTP utilizando métodos `GET`, `POST`, `PUT`, `DELETE`, `PATCH`, `OPTIONS` e `HEAD`. Uma das formas de fazer isso é utilizando funções assíncronas. Para por em pratica vamos realizar a seguir uma requisição pelos próximos lançamentos de filmes na [API do TheMovieDB](https://www.themoviedb.org/documentation/api) utilizando o método `async/await`. 

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
Recebemos como resultado uma lista em formato JSON em que cada objeto representa um filme que será lançado em breve:

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
Dessa forma podemos utilizar o modulo Axios para em nossos projetos para realizar requisições HTTP promised-based de forma simples e rápida.

<div style="text-align: right">

###### []'s 
