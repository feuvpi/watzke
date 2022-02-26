---
title: Criando um loader a partir de CSS puro
date: "2022-02-26T22:40:32.169Z"
description: "Utilizando CSS puro e simples para criar belas animações de carregamento."
---

<div style="text-align: justify">

##### Vamos desenvolver uma animação de carregamento - loader utilizando CSS puro e simples.

<div class="item"><i class="loader --1 animation"></i></div>

Primeiramente precisamos de um componente html para receber CSS.

```html
<div class="item">
  <i class="loader --1"></i>
</div>
```

Ainda não visualiza-se o componente, o mesmo não possui conteúdo e ainda não recebeu nenhuma estilização.

Partindo para o nosso código CSS, vamos iniciar definindo a cor e tamanho do nosso loader, além de configurações de posição e alinhamento no grid:

```css
.loader {
  --color: white;
  --size-mid: 6vmin;

  display: block;
  position: relative;
  width: 50%;
  display: grid;
  place-items: center;
}
```
Utilizar unidades como `vmin`, `vmax` e `rem` proporciona responsividade imediata à mudanças de proporção da viewport sem a necessidade de se utilizar `media queries`.

Para a criação do loader iremos utilizar os pseudo-elementos `before` e `after`. Pseudo-elementos são palavras especiais no css que permitem estilizar determinadas partes do componentes selecionado. Os pseudo-elementos `before` e `after` podem ser utilizados para injetar conteúdo antes ou depois de um componente. 

Utilizaremos esses elementos associados com configurações de posição para criar duas camadas - ou layers no nosso componente. Iremos estilizar essas duas layers de formas diferentes para a criação do loader.

```css
.loader::before,
.loader::after {
  content: "";
  box-sizing: border-box;
  position: absolute;
}
```

Acabamos de criar dois elementos que virão logo antes e depois de todo e qualquer componente da nossa página que possuir a classe "loader". A questão aqui é que até agora esse elementos não possuem conteúdo.

Uma configuração importante é a posição em absoluto. Como citado anteriormente, isto irá garantir que os dois elementos iniciem na mesma posição. Dessa forma, poderemos usa-los como layers.

A configuração `border-box` faz com que o `width` do componente em questão seja a soma do conteúdo, do padding e da borda.

Com nossas duas layers, vamos começar a injetar um pouco de CSS para começar a construir nosso loader, começaremos pelo `before`.

```css
.loader.--1::before {
	width: var(--size-mid);
	height: var(--size-mid);
	border: 4px solid var(--color);
	border-top-color: transparent;
```
<div class="wrapper"><div class="notes">Agora finalmente podemos visualizar nosso loader ganhando forma:</div><div class="item">
  <i class="loader exemplo" style="width: var(--size-mid);height: var(--size-mid);border: 4px solid var(--color);border-top-color: transparent;"></i>
</div></div>

Com apenas alguns comandos de CSS como `width`, `height` e `border`, começamos a criar nossa animação. Utilizaremos o mesmo método para o `after`, apenas alterando suavemente algumas configurações. Para visualizar o resultado vamos comentar o código do `before` para que a camada não fique visível.

```css
.loader.--1::after {
  width: calc(var(--size-mid) - 2px);
  height: calc(var(--size-mid) - 2px);
  border: 2px solid transparent;
  border-top-color: var(--color);
}
```

<div class="wrapper"><div class="notes"><code>.loader.--1::before</code>:</div><div class="item">
  <i class="loader exemplo" style="width: calc(var(--size-mid) - 2px);height: calc(var(--size-mid) - 2px);border: 2px solid transparent;border-top-color: var(--color);"></i>
</div></div>

<div class="wrapper"><div class="notes"><code>::before</code> e <code>::after</code> juntos:</div><div class="item">
  <i class="loader --A" style="border-radius: 0%;"></i>
</div></div>



<div class="wrapper"><div class="notes">Para dar um formato circular, uma opção é adicionar a configuração <code>`border-radius: 100%`</code> em ambos os blocos que acabamos de criar:</div><div class="item"><i class="loader --1"></i></div></div>

Para continuar a construção do nosso loader precisamos criar uma animação de rotação e aplicar a cada uma das layers, mas de forma que elas rotacionem em sentidos e velocidades diferentes. Utilizaremos a propriedade CSS `transform` e o comando rotate.

```css
@keyframes loader-1 {
	100% {
		transform: rotate(1turn);
	}
```
Para aplicar essa animação nos nossos layers, vamos inserir os seguintes comandos em cada um dos blocos `::before` e `::after`:

```css
animation: loader-1 0.6s linear reverse infinite

animation: loader-1 1s linear infinite
```
<div class="wrapper"><div class="notes">Agora sim, o loader está pronto para ser utilizado em nossas aplicações:</div><div class="item"><i class="loader --1 animation"></i></div></div>

Aprendi a como desenvolver esse loader no CodePen do @Jenning, [Simple CSS Loaders](https://codepen.io/jenning/pen/YzNmzaV). Lá é possivel aprender a fazer outros CSS loaders como este.

<div style="text-align: right">

###### []'s

