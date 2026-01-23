---
Created: 2025-03-06
tags:
  - Construir
---
**O método** `flatMap()` **em JavaScript combina** `map()` **e** `flat()` **em uma única operação, ideal para transformar e achatar arrays em um único nível.**

Sintaxe base: 
``` Js
const novoArray = arrayOriginal.flatMap((elemento, indice, array) => {
	//...
})


```


Exemplo 1:

``` Js
const numeros = [1, 2, 3];
const resultado = numeros.flatMap(x => [x, x * 2]);
console.log(resultado); // [1, 2, 2, 4, 3, 6]

```

Diferença com o MAP:

```js
const arr = [1, 2, 3];

arr.map(x => [x * 2]); 
// Resultado: [[2], [4], [6]]

arr.flatMap(x => [x * 2]); 
// Resultado: [2, 4, 6]

```


Aplicação com string:

``` Js
const frases = ["Olá mundo", "JS é legal"];
const palavras = frases.flatMap(frase => frase.split(" "));
console.log(palavras); // ["Olá", "mundo", "JS", "é", "legal"]

```