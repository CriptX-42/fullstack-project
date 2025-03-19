---
Created: 2025-03-19
---
### Fases



> [!NOTE] Para lembrar
> 1️⃣ **Criação** → Definição do Observable (**sem execução**).  
2️⃣ **Execução** → O Observable emite valores quando assinado.  
3️⃣ **Finalização** → O Observable **se completa** ou **lança um erro**.  
4️⃣ **Cancelamento** (opcional) → Chamando `unsubscribe()`, a assinatura é


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


### Finalização (Completion ou Error)

#### Complete

- Exemplo

```
const obs = new Observable(observer => {
  observer.next('Dado recebido');
  observer.complete(); // Finaliza a stream
  observer.next('Este dado nunca será emitido');
});

obs.subscribe({
  next: value => console.log(value),
  complete: () => console.log('Stream encerrada'),
});

```

> [!Example] Saída
Dado recebido
Stream encerrada


#### Erro

```
const obsWithError = new Observable(observer => {
  observer.next('Dado 1');
  observer.error('Algo deu errado!');
  observer.next('Este valor não será emitido');
});

obsWithError.subscribe({
  next: value => console.log(value),
  error: err => console.error('Erro:', err),
  complete: () => console.log('Isso nunca será chamado'),
});

```

> [!Example] Saída
Dado 1
Erro: Algo deu errado!



---

#### Cancelamento

```
import { interval } from 'rxjs';

const subscription = interval(1000).subscribe(value => {
  console.log('Valor:', value);
});

// Cancela a assinatura após 5 segundos
setTimeout(() => {
  subscription.unsubscribe();
  console.log('Observable cancelado');
}, 5000);

```

> [!Example] Saída
Valor: 0
Valor: 1
Valor: 2
Valor: 3
Valor: 4
Observable cancelado
