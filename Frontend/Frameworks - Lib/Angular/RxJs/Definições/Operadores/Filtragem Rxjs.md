---
Created: 2025-03-19
---
---

### Operadores de Filtragem
| Operador       | Descrição                                                 | Exemplo               |
| -------------- | --------------------------------------------------------- | --------------------- |
| `filter`       | Filtra valores que não atendem a uma condição.            | `filter(x => x > 10)` |
| `first`        | Emite apenas o primeiro valor.                            | `first()`             |
| `debounceTime` | Ignora valores rápidos e espera um tempo antes de emitir. | `debounceTime(300)`   |

```
import { of } from 'rxjs';
import { filter } from 'rxjs/operators';

of(5, 10, 15, 20)
  .pipe(filter(x => x > 10))
  .subscribe(console.log);
// Saída: 15 20

```
