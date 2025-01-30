---
Created: 2025-01-30
---

> [!NOTE] Regras
> 1. Em um **método** ele não pode apresentar corpo
> 2. Métodos abstratos só podem existir dentro de classes abstratas

Imagine que numa superclasse temos o método 

```
public abstract class Funcionario {  
    protected String nome;  
    protected double salario;  
  
    public Funcionario(String nome, double salario) {  
        this.nome = nome;  
        this.salario = salario;  
        calculaBonus(); // obrigatoriedade de implementação do 'calculaBonus'em todas as classes filhas 
    }  
  
    public abstract void calculaBonus();  
  
}
```


Um exemplo do nosso contrato *Gerente* quando não implementarmos calculaBonus que é obrigatório:

![[Pasted image 20250130174343.png]]

Agora quando cumprimos o contrato: 

```
public class Gerente extends Funcionario {  
    public Gerente(String nome, double salario) {  
        super(nome, salario);  
    }  
  
    @Override  
    public void calculaBonus() {  
        this.salario += this.salario * 0.10;  
    }  
  
  ...
}
```