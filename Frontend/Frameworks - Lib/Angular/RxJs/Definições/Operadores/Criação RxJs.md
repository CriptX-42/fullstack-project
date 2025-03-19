---
Created: 2025-03-19
---

| Operador | Descrição                                                       | Exemplo         |
| -------- | --------------------------------------------------------------- | --------------- |
| of       | Cria um Observable a partir de valores síncronos.               | of(1, 2, 3)     |
| from     | Converte uma estrutura iterável (array, Promise) em Observable. | from([1, 2, 3]) |
| interval | Emite valores em intervalos de tempo definidos.                 | interval(1000)  |
| timer    | Emite um valor após um tempo específico.                        | timer(2000)     |

```
import { of } from 'rxjs';

of('A', 'B', 'C').subscribe(console.log);
// Saída: A B C

```