---
Created: 2025-05-07
---
---

### Definição

Basicamente uma forma de executar um valor, pausar e retomar. Executando valores sob demanda (lazy evaluation). São definidos com `function` e a palavra chave `yeld`.

``` Js
function* contador() {
  yield 1;
  yield 2;
  yield 3;
}

const gen = contador();

console.log(gen.next()); // { value: 1, done: false }
console.log(gen.next()); // { value: 2, done: false }
console.log(gen.next()); // { value: 3, done: false }
console.log(gen.next()); // { value: undefined, done: true }

```

### ✅ Características importantes

- `function*` define um generator.
- `yield` pausa a função e retorna um valor.
- `.next()` retoma a função a partir de onde parou.
- Retorna um objeto `{ value, done }`.

