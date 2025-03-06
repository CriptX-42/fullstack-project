#### ReduceRight(callback, initialValue?)

É o reduce mas começa no final do Array

```
const numeros = [1, 2, 3, 4];
const resultado = numeros.reduceRight((acumulador, num) => acumulador - num, 0);
console.log(resultado); // -10

```