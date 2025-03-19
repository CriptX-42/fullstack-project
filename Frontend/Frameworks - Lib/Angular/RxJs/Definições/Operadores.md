---
Created: 2025-03-19
tags:
  - Dicionário
---
### Categorias
As mais usadas no angular

| Categoria              | Descrição                                                                        |
| ---------------------- | -------------------------------------------------------------------------------- |
| **Criação**            | Criam novos Observables (ex: `of`, `from`, `interval`)                           |
| **Transformação**      | Modificam valores emitidos (ex: `map`, `scan`)                                   |
| **Filtragem**          | Filtram valores indesejados (ex: `filter`, `debounceTime`)                       |
| **Combinação**         | Mesclam múltiplos Observables (ex: `merge`, `concat`)                            |
| **Multicasting**       | Compartilham um Observable entre múltiplos observadores (ex: `share`, `publish`) |
| **Tratamento de Erro** | Lidam com erros (ex: `catchError`, `retry`)                                      |

### Operadores de criação
- [[Criação RxJs]]

### Operadores de transformação
- [[Transformação Rxjs]]

### Operadores de filtragem
- [[Filtragem Rxjs]]

### Operadores de combinação
- [[Combinação Rxjs]]

### Operador Multicasting

| Operador  | Descrição | Exemplo |
|-----------|----------|---------|
| `share`   | Compartilha um Observable entre múltiplos assinantes. | `obs.pipe(share())` |
| `publish` | Permite criar uma versão multicast de um Observable. | `obs.pipe(publish())` |

### Operador de tratamento de erro
- [[Tratamento de erro Rxjs]]