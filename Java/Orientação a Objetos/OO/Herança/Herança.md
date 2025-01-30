---
Created: 2025-01-29
tags:
  - Dicionário
---
#### Guia
1. [[Super]]
2. [[Protected]]
3. [[Bloco de inicialização herança|Bloco de inicialização herança]]

#### Aplicabilidade

> [!NOTE] Atenção ao aplicar Herança
> Ela pode facilmente aumentar o acoplamento dos seus objetos. Dificultando até na escalabilidade 
> Herança múltipla não existe em java


- Imagine que temos um objeto 'Pessoa' e outro objeto 'endereço'. Quando aplicamos outro objeto chamado 'Funcionario' logo notamos que um funcionario tem endereço e é uma pessoa. Logo podemos transcrever isso como:

- Pessoa:
```
public class Pessoa {  
    public String nome;  
    public String cpf;  
    private Endereco endereco;  
  
    public String getNome() {  
        return nome;  
    }  
  
    public void setNome(String nome) {  
        this.nome = nome;  
    }  
  
    public String getCpf() {  
        return cpf;  
    }  
  
    public void setCpf(String cpf) {  
        this.cpf = cpf;  
    }  
  
    public Endereco getEndereco() {  
        return endereco;  
    }  
  
    public void setEndereco(Endereco endereco) {  
        this.endereco = endereco;  
    }  
}
```

- Endereço: 
```
public class Endereco {  
    private String rua;  
    private String cep;  
  
    public String getRua() {  
        return rua;  
    }  
  
    public void setRua(String rua) {  
        this.rua = rua;  
    }  
  
    public String getCep() {  
        return cep;  
    }  
  
    public void setCep(String cep) {  
        this.cep = cep;  
    }  
  
}
```

- Funcionário ===Estendendo 'Pessoa'===:
```
public class Funcionario extends Pessoa {  
    public double salario;  
  
    public double getSalario() {  
        return salario;  
    }  
  
    public void setSalario(double salario) {  
        this.salario = salario;  
    }  
}
```

> Logo ele vai ter todos os atributos de pessoa e endereço.



