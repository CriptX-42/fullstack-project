---
Created: 2025-03-16
---
### Conceito

São estruturas prontas e fornecidas pela linguagem para facilitar operações comuns, como por exemplo manipulação de strings, números, arrays e datas.


#### Objetos Globais Principais

- O **pai** de todos os objetos no JavaScript.
- Propriedades e métodos fundamentais para todos os objetos.

🔹 **Exemplo:**

```
const pessoa = { nome: "Alice", idade: 25 };
console.log(Object.keys(pessoa)); // ["nome", "idade"]
console.log(Object.values(pessoa)); // ["Alice", 25]
console.log(Object.entries(pessoa)); // [["nome", "Alice"], ["idade", 25]]

```

#### Arrays

🔹 **Exemplo:**

```
const numeros = [1, 2, 3, 4, 5];
console.log(numeros.length); // 5
console.log(numeros.map(n => n * 2)); // [2, 4, 6, 8, 10]
console.log(numeros.filter(n => n > 2)); // [3, 4, 5]
console.log(numeros.includes(3)); // true

```

### Number

```
const num = 42.5678;
console.log(num.toFixed(2)); // "42.57"
console.log(Number.isInteger(num)); // false
console.log(Number.parseInt("123px")); // 123
console.log(Number.parseFloat("3.14text")); // 3.14

```

#### Math

🔹 **Exemplo:**

```
console.log(Math.PI); // 3.141592653589793
console.log(Math.sqrt(16)); // 4
console.log(Math.pow(2, 3)); // 8
console.log(Math.floor(4.7)); // 4
console.log(Math.random()); // Número aleatório entre 0 e 1

```

#### Date

🔹 **Exemplo:**

```
const agora = new Date();
console.log(agora.toISOString()); // Data no formato ISO
console.log(agora.getFullYear()); // Ano atual
console.log(agora.getMonth() + 1); // Mês atual (começa do 0)
console.log(agora.getDay()); // Dia da semana (0 = domingo)

```

#### RegExp

🔹 **Exemplo:**

```
const regex = /java/i; // Case insensitive
console.log(regex.test("JavaScript")); // true
console.log("Aprendendo JavaScript".match(regex)); // ["Java"]

```


#### Json

🔹 **Exemplo:**

```
const dados = { nome: "Alice", idade: 25 };
const json = JSON.stringify(dados); // Converte para string JSON
console.log(json); // '{"nome":"Alice","idade":25}'

const obj = JSON.parse(json); // Converte de volta para objeto
console.log(obj.nome); // "Alice"

```