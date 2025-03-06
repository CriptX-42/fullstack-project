#### Some
Verifica se ao menos um passa na condição, caso passe ele retorna *true* se não passar, já sabe, é *false*

```
const numeros = [1, 2, 3];
const temPar = numeros.some(num => num % 2 === 0);
console.log(temPar); // true
```