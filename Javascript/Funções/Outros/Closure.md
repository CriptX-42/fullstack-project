---
Created: 2025-06-01
---
---
### Definição
Uma função que lembra da criação mesmo depois que o ambiente foi encerrado.
Não é uma forma "procedural".

Um exemplo:

``` Javascript
function saudacao(nome) {
  return function() {
    console.log(`Olá, ${nome}!`);
  };
}

const saudarJoao = saudacao('João');
saudarJoao(); // "Olá, João!"

```


> [!NOTE] Utilidade 
> - **Encapsulamento** (variáveis "privadas")
>- **Funções de fábrica**
>- **Manutenção de estado sem objetos**
>- **Callbacks e funções assíncronas** (como em `setTimeout`, `fetch`, etc.)
