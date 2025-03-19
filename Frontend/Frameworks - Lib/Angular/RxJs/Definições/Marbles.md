---
Created: 2025-03-19
---
### Definição
São basicamente diagramas para entender o fluxo assíncronos da nossa execução de forma visual, nos ajudando até nos testes unitários. Igual na imagem a seguir:

[Retirados do rxmarbles](https://rxmarbles.com/)

![[Pasted image 20250319121905.png]]

🔵 **Linha do tempo** → Representa a progressão do tempo, da esquerda para a direita.  
⚫ **Eventos (mármores)** → Cada círculo representa um valor emitido pelo Observable.  
🚀 **Operadores** → Transformam os valores ao longo do tempo.  
🔴 **Completação** → Um traço vertical (`|`) indica que o Observable foi concluído.

- Exemplo básico
```
--1--2--3--4--|   // Observable emitindo os valores 1, 2, 3, 4 e depois se completa
```

### Exemplo em alguns usos

#### Map

```
import { of } from 'rxjs';
import { map } from 'rxjs/operators';

of(1, 2, 3)
  .pipe(map(x => x * 10))
  .subscribe(console.log);

```


> [!Example] Saída
```
Entrada:  --1--2--3--|
Operação:     map(x => x * 10)
Saída:    --10-20-30-|
```


---

#### Filter
```
import { of } from 'rxjs';
import { filter } from 'rxjs/operators';

of(1, 2, 3, 4, 5)
  .pipe(filter(x => x % 2 === 0))
  .subscribe(console.log);

```

> [!Example] Saída
```
Entrada:  --1--2--3--4--5--|
Operação:     filter(x % 2 === 0)
Saída:    -----2-----4------|

```



---

#### mergeMap()

```
import { of } from 'rxjs';
import { delay, mergeMap } from 'rxjs/operators';

of('A', 'B')
  .pipe(mergeMap(x => of(`${x}1`, `${x}2`).pipe(delay(100))))
  .subscribe(console.log);

```

> [!Example] Saída
```
Entrada:  --A--B--|
Operação:    mergeMap(x => [x1, x2])
Saída:    --A1-A2-B1-B2--|

```

