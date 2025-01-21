## Explicação sobre as [[Varáveis]]

- Só existe dentro do bloco
- Pode ser reatribuído um valor
- Sofre [[Hoisting]] e da erro ao acessar antes de declarar, igual ao [[Const]] 

Exemplo de ==temporal dead zone==

```
console.log(teste) // ReferenceError: teste is not defined
let teste = []
```
