---
Created: 2025-02-03
---
#### forEach(callback)

- Executa uma função para cada elemento, sem retorno

```
const num = [12,42,3];
num.forEach(num => {
	console.log(num) => //12, 42, 3
})
```


#### map(callBack)

- Cria um novo array com o resultado aplicado a cada elemento

```
const num = [1,2,3];
const triplo = num.map(num => num * 3)
Saída:
console.log(triplo) // 3 , 6 , 9
```


#### filter(callback)

- Cria um novo array com elementos condicionais que atendem o callback

```
const num = [42, 3, 2];
num.filter(num => {
  if(num === 42) {
    return num
  }
})
Saída: 
[ 42 ]
```


#### reduce

```
const number = [1, 2];
const soma = number.reduce((acumulador, num) => acumulador + num, 0);
console.log(soma); // 10
```

> Acumulador: armazena o valor acumulado durante a iteração
> num: elemento atual
> 0: valor inicial do acumulador

#### ReduceRight(callback, initialValue?)

É o reduce mas começa no final do Array

```
const numeros = [1, 2, 3, 4];
const resultado = numeros.reduceRight((acumulador, num) => acumulador - num, 0);
console.log(resultado); // -10

```


#### Every

Se tudo passar na condição, retorna *true* caso contrario *false*

```
const numeros = [2, 4, 6];
const todosPares = numeros.every(num => num % 2 === 0);
console.log(todosPares); // true

```

#### Some
Verifica se ao menos um passa na condição, caso passe ele retorna *true* se não passar, já sabe, é *false*

```
const numeros = [1, 2, 3];
const temPar = numeros.some(num => num % 2 === 0);
console.log(temPar); // true
```