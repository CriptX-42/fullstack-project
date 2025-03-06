---
Created: 2025-03-06
---
### Copias de Objetos


| Método            | Cópia Profunda? | Mantém Métodos? | Performance    |
| ----------------- | --------------- | --------------- | -------------- |
| `...` (spread)    | ❌ Não           | ✅ Sim           | 🚀 Rápido      |
| Object.assign()   | ❌ Não           | ✅ Sim           | 🚀 Rápido      |
| JSON.stringify()  | ✅ Sim           | ❌ Não           | 🐢 Lento       |
| structuredClone() | ✅ Sim           | ❌ Não           | ⚡ Muito Rápido |
| _.cloneDeep()     | ✅ Sim           | ✅ Sim           | 🏎️ Rápido     |


> Cópias rasas (Shallow Copy)

> [!Warning] Isso é uma shallow Copy
> Funciona apenas para **cópias rasas** (shallow copy), ou seja, **objetos aninhados ainda serão referenciados!**

É muito comum se pensar que intuitivamente quando estamos lidando com objetos em memoria, podemos criar cópias com referencia deles, o que é errado. Um bom exemplo disso:

```
const obj1 = { nome: "João", idade: 30 };
const obj2 = obj1; // Apenas referência, NÃO é uma cópia

obj2.nome = "Maria"; 

console.log(obj1.nome); // "Maria" (obj1 também foi alterado!)

```

- Usando spread Operator é a forma mais correta de se criar uma cópia segura:

```
const obj1 = { nome: "João", idade: 30 };
const obj2 = { ...obj1 };

obj2.nome = "Maria";

console.log(obj1.nome); // "João" (obj1 não foi alterado!)
console.log(obj2.nome); // "Maria"

```

#### Object Assign

```
const obj1 = { nome: "João", idade: 30 };
const obj2 = Object.assign({}, obj1);

obj2.nome = "Maria";

console.log(obj1.nome); // "João" (obj1 não foi alterado!)

```

> Use sempre spread quando precisar de uma sintaxe limpa e moderna, e use sempre Object.Assign quando precisar de compatibilidaded



### Copia profunda (Deep Copy)

#### JSON 

```
const obj1 = { nome: "João", endereco: { cidade: "São Paulo" } };
const obj2 = JSON.parse(JSON.stringify(obj1));

obj2.endereco.cidade = "Rio de Janeiro";

console.log(obj1.endereco.cidade); // "São Paulo" (Agora está seguro!)

```


> [!Warning] Lado bom e ruim
> ✔ **Vantagem:** Resolve o problema da **cópia rasa**.  
❌ **Desvantagens:**
>- Perde métodos do objeto (`function` não é clonada).
>- Pode dar erro se o objeto tiver valores `undefined`, `Symbol` ou `BigInt`.

##### `structuredClone()` (Nova solução moderna)

```
const obj1 = { nome: "João", endereco: { cidade: "São Paulo" } };
const obj2 = structuredClone(obj1);

obj2.endereco.cidade = "Rio de Janeiro";

console.log(obj1.endereco.cidade); // "São Paulo" (Não foi alterado!)

```

> Ele não copia o métodos function, assim como json, mas mantem os dados
> Só está disponivel no Node.js 17+
