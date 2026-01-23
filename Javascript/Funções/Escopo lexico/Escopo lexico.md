---
Created: 2025-02-20
tags:
---
-------------

Um conceito simples em JS, basicamente define **as varaveis e funções** são acessiveis com base em onde elas foram declaradas no código. E onde não são chamadas.

Quando o javascript interpreta nosso código, ele lê toda a estrutura, associa blocos de escopo com base na disposição em que as variaveis foram declaradas no código.

``` js
function fora() {
  const mensagem = "Olá do escopo externo!";

  function dentro() {
    console.log(mensagem); // consegue acessar 'mensagem'
  }

  return dentro;
}

const func = fora();
func(); // "Olá do escopo externo!"

```

### Pq esse nome engraçado? 
Vem do fato que o escopo é determinado **durante a leitura do código**, e não em tempo de execução:
 - A função lembra do ambiente que foi criada.
 - Não importa onde você chama a função, importa onde ela foi definida

