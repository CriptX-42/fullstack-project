---
Created: 2025-11-09
---
---

#### Tornando um objeto imutável

``` js
const pessoa = Object.freeze({ nome: "Ana" });
pessoa.nome = "João"; // Ignorado em modo estrito

```
- Impede modificações nas propriedades.
- **Não protege objetos aninhados** — use `deepFreeze()` para isso.
