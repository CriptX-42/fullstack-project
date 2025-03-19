---
Created: 2025-03-19
---
### Definição
Basicamente o que define o comportamento entre um observavel e um observador, para lidar com fluxos assincronos e de forma reativa, isso é o puro suco da programação orientada a eventos meu amigo! Deveria ser considerado uma maravilha do mundo.

#### Como funciona o padrão observable? 
- **Observable (Observável)** → Representa uma **fonte de dados** que pode emitir valores ao longo do tempo.
- **Observer (Observador)** → Um consumidor que **escuta** e **reage** aos valores emitidos pelo Observable.
- **Subscription (Assinatura)** → Uma conexão entre o Observer e o Observable.
- **Operators (Operadores)** → Métodos usados para transformar, filtrar e combinar fluxos de dados.
- **Unsubscribe (Cancelar inscrição)** → Quando o Observer não precisa mais receber atualizações, ele se desconecta do Observable.


### Um exemplo simples

```
import { Observable } from 'rxjs';

const observable = new Observable(observer => {
  observer.next('Primeiro valor');
  observer.next('Segundo valor');
  setTimeout(() => {
    observer.next('Valor assíncrono');
    observer.complete();
  }, 2000);
});

observable.subscribe({
  next: value => console.log(value),
  complete: () => console.log('Observable completado!')
});

```


> [!Example] Saída
```

Primeiro valor
Segundo valor
(2 segundos depois...)
Valor assíncrono
Observable completado!

```
