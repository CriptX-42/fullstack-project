---
Created: 2025-03-19
---

| Operador    | Descrição | Exemplo |
|------------|----------|---------|
| `catchError` | Captura erros e retorna um novo Observable. | `catchError(err => of('Erro tratado'))` |
| `retry`     | Reexecuta um Observable em caso de erro. | `retry(3)` |
- Exemplo: Usando `catchError`
```
import { of, throwError } from 'rxjs';
import { catchError } from 'rxjs/operators';

throwError('Erro!')
  .pipe(catchError(err => of('Erro tratado')))
  .subscribe(console.log);
// Saída: Erro tratado

```