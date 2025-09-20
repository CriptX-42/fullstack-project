---
Created: 2025-09-20
aliases:
tags:
  - Aprofundar
---
---
### Arquitetura hexagonal

 ![[Pasted image 20250920200237.png]]

- O **port** é uma interface que via implementar `read` e `white`, e ele precisa ser agnostico,  
- O **adapter** é quem vai ser responsável por traduzir para algo que seja compreensível para uma api ou db por exemplo
Isso tanto vale para o `input` quanto o `output`


| Pros                         | Contras      |
| ---------------------------- | ------------ |
| separation of concerns (SOC) | Complexidade |
| Testabilidade                |              |

> [!NOTE] Dicas
>
>- Sem dominios anemicos
>- Interfaces do tamanho certo


----
- Pseudo código

Porta de saída (interface)
``` Java
public interface ContaRepository {
    Conta buscarPorId(String id);
    void salvar(Conta conta);
}

```

Caso de uso (dominio):

``` Java
public class Depositar {
    private final ContaRepository repo;

    public Depositar(ContaRepository repo) {
        this.repo = repo;
    }

    public void executar(String idConta, BigDecimal valor) {
        Conta conta = repo.buscarPorId(idConta);
        conta.depositar(valor);
        repo.salvar(conta);
    }
}

```

Adaptador (banco de dados por exemplo): 

``` Java
public class ContaRepositoryJPA implements ContaRepository {
    // implementação usando JPA
}
```


---

### Em spring

Entidade
``` Java
package com.exemplo.contas.domain;

import java.math.BigDecimal;

public class Conta {
    private String id;
    private BigDecimal saldo;

    public Conta(String id, BigDecimal saldoInicial) {
        this.id = id;
        this.saldo = saldoInicial;
    }

    public void depositar(BigDecimal valor) {
        if (valor.compareTo(BigDecimal.ZERO) <= 0) {
            throw new IllegalArgumentException("Valor deve ser positivo");
        }
        saldo = saldo.add(valor);
    }

    public String getId() { return id; }
    public BigDecimal getSaldo() { return saldo; }
}

```


Porta de saída (Interface)
``` Java
package com.exemplo.contas.domain;

public interface ContaRepository {
    Conta buscarPorId(String id);
    void salvar(Conta conta);
}

```

Caso de uso (Aplicação)
``` Java
package com.exemplo.contas.application;

import com.exemplo.contas.domain.Conta;
import com.exemplo.contas.domain.ContaRepository;
import java.math.BigDecimal;

public class DepositarService {
    private final ContaRepository repo;

    public DepositarService(ContaRepository repo) {
        this.repo = repo;
    }

    public void executar(String idConta, BigDecimal valor) {
        Conta conta = repo.buscarPorId(idConta);
        conta.depositar(valor);
        repo.salvar(conta);
    }
}
```