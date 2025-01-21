## Explicação sobre as [[Varáveis]]

- Atribuído num escopo de bloco
- Quando atribuímos um valor primitivo , não pode ser reatribuido
- SE estiver atribuido um [[Array]] ou [[Objeto]]. Seus elementos podem ser modificados
- Sofre [[Hoisting]] igual o [[Let]] e com ==temporal dead zone==


Exemplo de erro para modificadores
```
	- const x = 2
	- x=20 // ERRO
```

