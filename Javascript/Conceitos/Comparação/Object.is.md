---
Created: 2025-02-05
---

> [!NOTE] Definição
> Método usado para comparar dois valores de forma precisa. Ele verifica se é igual com algumas diferença do operador `===`
> Sintaxe: `Object.is(value1, value2)`


#### Diferença entre Object.is e `===`

| Caso          | Object.is() | ===   |
| ------------- | ----------- | ----- |
| NaN=== Nan    | true        | false |
| +0 === -0     | false       | true  |
| null === null | true        | true  |
| 5 === 5       | true        | true  |
Exemplos:

```
console.log(Object.is(5, 5));           // true
console.log(Object.is('text', 'text')); // true
console.log(Object.is(NaN, NaN));       // true (diferente de ===)
console.log(Object.is(+0, -0));         // false (diferente de ===)
console.log(Object.is(null, null));     // true

```
