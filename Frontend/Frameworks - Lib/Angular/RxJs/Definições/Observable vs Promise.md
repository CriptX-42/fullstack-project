---
Created: 2025-03-19
---
| Característica        | Observable                               | Promise            |
| --------------------- | ---------------------------------------- | ------------------ |
| **Vários valores**    | ✅ Sim                                    | ❌ Não (somente um) |
| **Cancelável**        | ✅ Sim (`unsubscribe()`)                  | ❌ Não              |
| **Operadores**        | ✅ Sim (como `map`, `filter`, `mergeMap`) | ❌ Não              |
| **Lazy Execution**    | ✅ Sim (só executa quando alguém assina)  | ✅ Sim              |
| **Suporte a eventos** | ✅ Sim                                    | ❌ Não              |
