---
Created: 2025-04-11
---

----------
###  **O que é "renderização" no React?**

Renderizar, no contexto do React, é o ato de **executar a função do seu componente** e **converter aquilo em elementos que o navegador entende** (HTML no final das contas).

```
function MeuComponente() {
  return <h1>Olá, mundo!</h1>;
}

```

O React chama `MeuComponente()`, vê que retorna `<h1>Olá, mundo!</h1>` e transforma isso em algo que o navegador possa mostrar.

React é totalmente declarativo, não é imperativo. Você não precisa dizer como montar uma UI, você diz oq quer que apareça, deixa o react cuidar do resto.

```
{isLoggedIn ? <Dashboard /> : <Login />}

```
E o React decide **o que renderizar**, com base nesse estado.


### Virtual DOM
O react não **manipula diretamente o DOM real** (isso é lento), no lugar disso:
- Ele cria uma versão em memória do dom, chamada **VIRTUAL DOM**
- Quando algo muda (como um estado), o React:
	- Re-renderiza o componente na memória.
    - Compara o novo Virtual DOM com o antigo (**diffing**).
    - Aplica só as mudanças necessárias no DOM real (**reconciliação**).
- 