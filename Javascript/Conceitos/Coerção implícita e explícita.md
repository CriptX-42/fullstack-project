---
Created: 2026-01-23
---
---
### Coerção implícita e explícita

- Implicita (JS converte sozinho)
- Explicita (vc está convertendo)

Por base o JS tenta adivinhar o que você quer:

``` Js
"5" + 2 // 52
```

Alguns tipos de comparação sem coerção:

``` js
"5" == 5        // true
0 == false     // true
null == undefined // true
[] == false    // true | Faz algum sentido?

```

`== ou !==` não tem um coerção, isso é comparação solta


Alguns exemplos de coerção explicita: 

``` js
Number("42")  // 42
+"42"         // 42
parseInt("42px") // 42

```

``` Js
// Implícita
if (value) {}

// Explícita
if (Boolean(value)) {}

```

