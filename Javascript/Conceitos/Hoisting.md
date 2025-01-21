É um comportamento do Javascript em que declarações de variáveis são movidas para o topo do escopo (seja global ou de função), na hora da compilação. E antes da execução do código

```
console.log(nome) // undefined
var nome = "Ricardo"
console.log(nome) // "Ricardo"
```

O Hosting também acontece com [[Let]] e [[Const]] mas entram num conceito de "temporal dead zone". Não podemos acessar antes de declarar no código