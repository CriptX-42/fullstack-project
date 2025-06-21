---
Created: 2025-06-21
---
----

### Definição
É basicamente um padrão que permite trocar o comportamento de um objeto em tempo de execução, sem precisar mudar o código dele.


> [!NOTE] Quando devemos usar?
>- Quando existem varias maneiras de realizar uma tarefa ou algorítimo, e não queremos 
> condiciais impregnadas nele  
>- Troca dinamica de comportamento 
>- Quando quiser seguir o ==Open/Closed== do SOLID
>

---

### Estrutura basica
- **Strategy (interface)** — Define a interface comum para todos os algoritmos.
- **Concrete Strategies (Implementações)** — Implementações específicas da interface Strategy, cada uma com um algoritmo diferente.
- **Context (Contexto)** — Mantém uma referência para um objeto Strategy e delega a ele o trabalho.

---

Um Exemplo:


A interface Strategy:
```ts
interface FreteStrategy {
  calcular(valor: number): number;
}
```

A implementação:

```ts
class FreteCorreios implements FreteStrategy {
  calcular(valor: number): number {
    return valor + 20;
  }
}

class FreteTransportadora implements FreteStrategy {
  calcular(valor: number): number {
    return valor + 35;
  }
}

class RetiradaNoLocal implements FreteStrategy {
  calcular(valor: number): number {
    return valor;
  }
}

```

A criação do contexto:

```ts
class CalculadoraDeFrete {
  private strategy: FreteStrategy;

  constructor(strategy: FreteStrategy) {
    this.strategy = strategy;
  }

  setStrategy(strategy: FreteStrategy) {
    this.strategy = strategy;
  }

  calcular(valor: number): number {
    return this.strategy.calcular(valor);
  }
}

```

O uso:

```ts
const pedido = new CalculadoraDeFrete(new FreteCorreios());
console.log(pedido.calcular(100)); // 120

pedido.setStrategy(new RetiradaNoLocal());
console.log(pedido.calcular(100)); // 100

pedido.setStrategy(new FreteTransportadora());
console.log(pedido.calcular(100)); // 135

```