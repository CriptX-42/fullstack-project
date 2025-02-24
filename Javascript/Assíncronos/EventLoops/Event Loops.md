---
tags:
  - Construir
---

> [!NOTE] Algumas dicas
> [Loupe](http://latentflip.com/loupe/?code=JC5vbignYnV0dG9uJywgJ2NsaWNrJywgZnVuY3Rpb24gb25DbGljaygpIHsKICAgIHNldFRpbWVvdXQoZnVuY3Rpb24gdGltZXIoKSB7CiAgICAgICAgY29uc29sZS5sb2coJ1lvdSBjbGlja2VkIHRoZSBidXR0b24hJyk7ICAgIAogICAgfSwgMjAwMCk7Cn0pOwoKY29uc29sZS5sb2coIkhpISIpOwoKc2V0VGltZW91dChmdW5jdGlvbiB0aW1lb3V0KCkgewogICAgY29uc29sZS5sb2coIkNsaWNrIHRoZSBidXR0b24hIik7Cn0sIDUwMDApOwoKY29uc29sZS5sb2coIldlbGNvbWUgdG8gbG91cGUuIik7!!!PGJ1dHRvbj5DbGljayBtZSE8L2J1dHRvbj4%3D) Essa ferramenta te ajuda a entender o que o JS faz por baixo dos panos 
> 


### Callback

- Uma forma de avisar o event loop que ele terminou de processar uma tarefa

### Event loop

- Basicamente a estrutura como o JS gerencia as tarefas, basicamente ele monitora as coisas que estão pra acontecer na linha de execução e as coisas que já estão prontas para serem executadas
- Exemplo, se eu tenho um callback, e qualquer outra tarefa depois disso, ele executa o callback e por mais que isso demore, já executa a tarefa posterior. 
- O Event Loop verifica toda hora que a pilha de call stack está vazia.

### Exemplo:

```
console.log("Início"); 
setTimeout(() => { console.log("Timeout"); }, 0); 

Promise.resolve().then(() => console.log("Promise resolvida")); 

console.log("Fim");
```


> [!Example] Saída
> ```
Início 
Fim 
Promise resolvida 
Timeout

> A promisse é uma prioridade de **Microtask Queue** então a prioridade é maior do que o setTimeout


> [!Tip] Para lembrar as prioridades
> - **Microtasks (alta prioridade)**: `Promise.then()`, `MutationObserver`, `queueMicrotask()`
> - **Macrotasks (baixa prioridade)**: `setTimeout`, `setInterval`, `setImmediate`, `I/O`, `MessageChannel`


![[Pasted image 20250224124803.png]]