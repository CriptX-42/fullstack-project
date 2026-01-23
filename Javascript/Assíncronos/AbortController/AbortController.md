---
Created: 2025-11-09
---
----
### Definição
Uma interface que cria um *sinal de cancelamento*, que quando passado para operações assincronas ( `fetch()` ), elas sejam abortadas antes de serem concluídas:

Controlador:
```js
const controller = new AbortController();
const signal = controller.signal;

```

Passando para o `fetch`:
``` js
fetch('https://api.exemplo.com/dados', { signal })
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(err => {
    if (err.name === 'AbortError') {
      console.log('Requisição cancelada!');
    } else {
      console.error('Erro:', err);
    }
  });

```

Efetuando o abort:

``` js
controller.abort(); // dispara o erro AbortError

```


Exemplo prático: 

``` js
const controller = new AbortController();
setTimeout(() => controller.abort(), 5000); // cancela após 5 segundos

fetch('https://api.exemplo.com/lento', { signal: controller.signal })
  .catch(err => {
    if (err.name === 'AbortError') {
      console.log('Timeout: requisição cancelada');
    }
  });

```