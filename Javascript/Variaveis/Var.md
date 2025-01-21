## Explicação sobre as [[Varáveis]]

- Possui escopo de função ou global. Não respeita a fronteira de bloco de código
- Pode ser reatribuída
- Pode se usar antes de declarar, mas cai no conceito de [[Hoisting]] mas sem a temporal dead zone

Inicializa quando compilado:
```
console.log(nome) // undefined
var nome = "Ricardo"
console.log(nome) // "Ricardo"
```