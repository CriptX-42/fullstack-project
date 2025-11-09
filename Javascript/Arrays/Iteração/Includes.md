---
Created: 2025-11-08
---
----

### Para que serve?

Ao fazer um exercicio do hackerhank me deparei com uma forma mais limpa de comparação entre arrays ou até mesmo em saber se determinada informação existe dentro de um array


``` javascript
const array = [1, 2, 3];

console.log(array.includes(2));
// Expected output: true

const pets = ["cat", "dog", "bat"];

console.log(pets.includes("cat"));
// Expected output: true

console.log(pets.includes("at"));
// Expected output: false


```

### Exemplo do exercício 

``` javascript
const vogal = ["a", "e","i","o","u"]
const palavra = "javascript"

const arrayTransform = palavra.split("")

const sequenciaVogal = arrayTransform.filter((item) => vogal.includes(item))
const sequenciaConsoante = arrayTransform.filter((item) => !vogal.includes(item))

console.log(sequenciaVogal)
// [ 'a', 'a', 'i' ]

console.log(sequenciaConsoante)

// [ 'j', 'v', 's', 'c', 'r', 'p', 't' ]
```