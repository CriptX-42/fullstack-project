---
Created: 2025-03-05
---
### Uso 
Ele basicamente é um operador que nos mostra que tipo é uma variável, ou até mesmo um valor. Ele retorna uma string indicando o tipo que estamos operando: 

```
console.log(typeof "Hello");   // "string"
console.log(typeof 42);        // "number"
console.log(typeof true);      // "boolean"
console.log(typeof undefined); // "undefined"
console.log(typeof null);      // "object"  (curiosidade: um bug histórico do JS)
console.log(typeof {});        // "object"
console.log(typeof []);        // "object"  (Arrays são objetos em JS)
console.log(typeof function(){}); // "function"
console.log(typeof Symbol("id")); // "symbol"
console.log(typeof BigInt(9007199254740991)); // "bigint"

```


> [!Danger] Cuidado
> - Null retorna *object*, pois isso é um erro do javascript
> - Arrays retornam "Object", Então se quisermos saber sobre um array, usamos `Array.isArray[]`
> - Funções retornam `Function`, mas na teoria são um objeto especial

