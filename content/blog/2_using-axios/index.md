---
title: Utilizando a dependêencia Axios para realizar requisições HTTP promise-based.
date: "2022-01-11T22:40:32.169Z"
description: "Utilizando a dependência Axios para comunicação com API's externas."
---
<div style="text-align: justify">

##### Nesse post iremos realizar uma requisição para uma API externa utilizando o protocolo HTTP atraves da dependência Axios.

## Sobre a dependência Axios

O Axios é um cliente HTTP promise-based para o node.js e para o browser. Utilizando essa ferramenta open-source é possivel realizar requisições HTTP em APIs externas de forma simples e objetiva.

## Instalando o Axios no Projeto

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


## Utilizando funções assincronas com axios para realizar solicitações externas

A dependência Axios permite realizar requisiçòes http utilizando metodos GET, POST, PUT, DELETE, PATCH, OPTIONS, HEAD. Uma das formas de fazer isso é utilizando funções assincronas. Abaixo iremos realizar uma consulta aos proximos lançamentos na [API do TheMovieDB](https://www.themoviedb.org/documentation/api) utilizando o metodo `async/await`. 

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
Dessa forma vimos rapidamente como podemos fazer o uso da dependência Axios em nossos projetos para realizar requisições HTTP promise-based de forma simples e rapida.

[]'s 
