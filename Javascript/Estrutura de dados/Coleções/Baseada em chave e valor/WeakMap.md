---
Created: 2025-03-11
---
### Definiçõa

Muito similar ao *map*, mas a **chave deve ser obrigatoriamente objetos**, e tem uma referencia muito fraca, ou seja, se o objeto for removido da memória, ele vai ser removido do WeakMap


> [!NOTE] Algumas notas
> - Apenas objetos podem ser chaves
> - Não existe métodos para iterar (**size**, **keys()**, **values()**, **entries()**)
> - O garbage collector pode remover a chave que não são mais referenciadas

```
const weakMap = new WeakMap();

let obj = { nome: 'Bob' };
weakMap.set(obj, 'Informações secretas');

console.log(weakMap.get(obj)); // "Informações secretas"

obj = null; // O objeto pode ser coletado pelo garbage collector

// Agora, a chave e o valor associados podem desaparecer

```

