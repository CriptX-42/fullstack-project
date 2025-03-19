---
Created: 2025-03-19
---
### Fases

#### Criação
Aqui o **Observable** é declarado, mas ainda **não está sendo executado**.

```
import { Observable } from 'rxjs';

const myObservable = new Observable(observer => {
  observer.next('Valor 1');
  observer.next('Valor 2');
  observer.complete();
});

```


📌 **Neste estágio, nada acontece!** O Observable só será executado quando houver uma **assinatura**.



---


#### Execução

Agora alguém assina o Observable usando `.subscribe()`, e ele começa a emitir valores.
```
myObservable.subscribe({
  next: value => console.log(value),
  complete: () => console.log('Observable completado!'),
});
```

> [!Example] Saída
> Valor 1
Valor 2
Observable completado!



---


### Finalização

