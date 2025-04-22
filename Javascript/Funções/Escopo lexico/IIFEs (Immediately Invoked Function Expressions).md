---
Created: 2025-04-22
---
------
São funções em JS que são criadas e definidas imediatamente após sua criação (você usava muito isso em 2015).

Sintaxe:

```
(function() {
  // código aqui dentro é executado imediatamente
})();

```

Ou mesmo:

```
(() => {
  // código executado imediatamente
})();

```


> [!Warning] Por que usar isso?
> Evita sujeira em escopo global, as variáveis não vazam pra outro lugar
> Criar escopos isolados para módulos ou lógicas 
> Executar os códigos apenas uma vez
>


> [!NOTE] E mais
> Da pra usar normalmente com async/await e promise, pq não daria? 
