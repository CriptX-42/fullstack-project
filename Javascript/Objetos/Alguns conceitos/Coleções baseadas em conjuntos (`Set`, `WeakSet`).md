---
Created: 2025-03-16
---
### Set
Essa estrutura armazena dados de valores únicos de qualquer tipo, seja primitivo ou objeto. 


> [!NOTE] Caracteristicas
> - **Valores únicos**: Não permite valores duplicados.
> - **Iterável**: Pode ser percorrido com `forEach`, `for...of` e convertido para arrays.
> - **Mantém a ordem de inserção**.
> - **Aceita qualquer tipo de dado** (strings, números, objetos, etc.).

🔹 **Exemplo:**


```
const set = new Set();

set.add(1);
set.add(2);
set.add(2); // Ignorado, pois já existe no conjunto
set.add("Hello");
set.add({ id: 1 });

console.log(set); // Set { 1, 2, 'Hello', { id: 1 } }

// Métodos úteis
console.log(set.has(2)); // true
console.log(set.size); // 4
set.delete(1); // Remove o valor 1
console.log(set); // Set { 2, 'Hello', { id: 1 } }

set.clear(); // Remove todos os elementos
console.log(set.size); // 0

```

#### Conversão entre set e Arrays

```
const numbers = [1, 2, 3, 3, 4, 5, 5];
const uniqueNumbers = [...new Set(numbers)];
console.log(uniqueNumbers); // [1, 2, 3, 4, 5]
```

### WeakSet
Igual ao `set` mas com algumas restrições


> [!NOTE] Caracteristicas
> - **Somente armazena objetos** (não aceita valores primitivos).
> - **Fraco (Weak)**: Os objetos armazenados podem ser coletados pelo _Garbage Collector_ se não houver mais referências a eles.
> - **Não é iterável**: Não pode ser percorrido com `forEach`, `for...of`, ou convertido para array.
> - **Sem tamanho (`size`)**: Não há como verificar quantos elementos existem no `WeakSet`.

```
const weakSet = new WeakSet();

let obj1 = { name: "Alice" };
let obj2 = { name: "Bob" };

weakSet.add(obj1);
weakSet.add(obj2);

console.log(weakSet.has(obj1)); // true

weakSet.delete(obj1); // Remove obj1 do WeakSet

console.log(weakSet.has(obj1)); // false

// obj2 será coletado pelo Garbage Collector quando não houver mais referências
obj2 = null;

```

### Principais diferenças

| Característica                                     | Set                     | WeakSet |
| -------------------------------------------------- | ----------------------- | ------- |
| Aceita valores primitivos                          | Sim                     | Não     |
| Aceita objetos                                     | Sim                     | Sim     |
| Garante valores únicos                             | Sim                     | Sim     |
| Permite iteração                                   | Sim (forEach... for of) | Não     |
| Pode armazenar objetos fracos (garbage collection) | Não                     | Sim     |
| Possui propriedade `size`                          | Sim                     | Não     |
- **Use `Set`** quando precisar armazenar valores únicos e precisar iterar sobre eles.
- **Use `WeakSet`** quando quiser armazenar objetos sem impedir sua remoção pelo _Garbage Collector_ (por exemplo, para rastrear referências temporárias sem risco de vazamento de memória).
