---
Created: 2025-03-10
---
#### Definição clara

Map é uma estrutura de dados que armazena chave/valor, permitindo qualquer tipo como valor **chave** (objetos e funções também).


> [!NOTE] Algumas coisas boas
> - Mantém a ordem do de inserção
> - As chaves podem ser de qualquer tipo, diferente dos objetos que só aceitam *string e symbol*
> - Possui métodos especificos para manipulação


```
const map = new Map();

map.set('nome', 'Alice');
map.set(42, 'Idade');
map.set({ id: 1 }, 'Objeto como chave');

console.log(map.get('nome')); // Alice
console.log(map.has(42)); // true
console.log(map.size); // 3

map.delete(42);
console.log(map.has(42)); // false

map.forEach((valor, chave) => {
  console.log(chave, valor);
});

```

