---
Created: 2025-05-02
---
----
Basicamente uma forma de exibir dados do **template HTML** no nosso componente. Ela utiliza a sintaxe {{ *expressão* }} para inserir valores no DOM.



```
<p>{{ 2 + 2 }}</p>                 <!-- 4 -->
<p>{{ nome.toUpperCase() }}</p>   <!-- transforma em maiúsculo -->
<p>{{ usuario.id }}</p>           <!-- acesso a objeto -->
<p>{{ lista.length }}</p>         <!-- acesso a propriedade -->

```



> [!Danger] Cuidado
> Não use coisas como `<p>{{ contador++ }}</p>` isso não funciona
> Não use lógicas muito pesadas chamando uma função também, pois isso é chamado cada vez que a view atualiza
> 
