---
Created: 2025-01-29
tags:
  - Aprofundar
  - Duvidas
---
### O que é
- Uma propriedade executada antes do construtor

> [!NOTE] Prioridade de inicialização
>  0. Bloco de inicialização estático da super classe é executado quando a JVM carregar classe pai
>  1. Bloco de inicialização estática da sub classe é executado quando a JVM carregar a classe filha
>  2. Alocado espaço em memória pro objeto
>  3. Cada atributo da superclasse é criado e inicializado com valores default ou que for passado da classe pai
>  4. Bloco de inicialização da superclasse é executado na ordem em que aparece
>  5. Construtor é executado da superclasse

### Aprofundar
https://www.youtube.com/watch?v=raAHfRdld0Y&list=PL62G310vn6nFIsOCC0H-C2infYgwm8SWW&index=76