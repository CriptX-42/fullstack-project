---
Created: 2025-03-19
---
### Sobre o Operador
Modificam os valores emitidos por um Observable.


| Operador   | Descrição | Exemplo |
|------------|----------|---------|
| `map`      | Transforma os valores emitidos. | `map(x => x * 10)` |
| `scan`     | Acumula valores ao longo do tempo (como `reduce`). | `scan((acc, x) => acc + x, 0)` |

```
import { of } from 'rxjs';
import { map } from 'rxjs/operators';

of(1, 2, 3)
  .pipe(map(x => x * 10))
  .subscribe(console.log);
// Saída: 10 20 30

```