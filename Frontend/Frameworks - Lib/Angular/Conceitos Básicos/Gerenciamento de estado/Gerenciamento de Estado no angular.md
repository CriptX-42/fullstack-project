---
Created: 2025-05-01
---
-----
### Interno 
```
export class MeuComponente {
  contador = 0;

  incrementar() {
    this.contador++;
  }
}

```

### Por serviços

```
@Injectable({ providedIn: 'root' })
export class EstadoService {
  private _contador = 0;

  get contador() {
    return this._contador;
  }

  incrementar() {
    this._contador++;
  }
}

```

Use em qualquer componente: 
```
constructor(public estado: EstadoService) {}

```


### Reativa

```
private contador$ = new BehaviorSubject<number>(0);

incrementar() {
  const valorAtual = this.contador$.value;
  this.contador$.next(valorAtual + 1);
}

getContador(): Observable<number> {
  return this.contador$.asObservable();
}

```

No componente:
```
this.estadoService.getContador().subscribe(valor => this.valor = valor);

```

### NgRX

Descrever sobre


#### **Signals (Angular 16+)**

Angular 16 introduziu `signals` como uma forma reativa de gerenciar estado localmente com menos boilerplate que RxJS.
(Nunca usei isso mas copiaram na cara dura do react)

```
import { signal } from '@angular/core';

contador = signal(0);

incrementar() {
  this.contador.update(c => c + 1);
}

```

