---
Created: 2025-03-19
---
Eles combinam múltiplos Observables num único fluxo:

### Operadores de Combinação
| Operador   | Descrição | Exemplo |
|------------|----------|---------|
| `merge`    | Mescla múltiplos Observables. | `merge(obs1, obs2)` |
| `concat`   | Executa Observables em sequência. | `concat(obs1, obs2)` |
| `combineLatest` | Emite valores combinados de múltiplos Observables. | `combineLatest([obs1, obs2])` |
| `forkJoin` | Espera todos os Observables completarem e retorna os últimos valores. | `forkJoin([obs1, obs2])` |
```
import { merge, of } from 'rxjs';

const obs1 = of(1, 2, 3);
const obs2 = of('A', 'B', 'C');

merge(obs1, obs2).subscribe(console.log);
// Saída: 1 2 3 A B C

```

