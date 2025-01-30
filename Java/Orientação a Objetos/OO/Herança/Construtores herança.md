---
Created: 2025-01-28
---

> [!NOTE] Imagine o problema
> Imagine que pessoa precisa ter um nome, por isso colocamos **nome** inserido no construtor do objeto *Pessoa*
> Logo nosso objeto *Funcionario* vai herdar essa obrigatoriedade. Como sanar isso?

- Simples, basta usar o [[Super]]. Ex:

```
public class Pessoa {  
    public String nome;  
	public String cpf;  
	private Endereco endereco;  
  
  
public Pessoa(String nome) {  
    this.nome = nome;  
}
...
	
}
```

Sugestão da IDE em *Funcionário*

![[Pasted image 20250129153926.png]]

Uso do super:

```
public class Funcionario extends Pessoa {  
    public double salario;  
  
    public Funcionario (String nome) {  
        super(nome);  //Super
    }  
  
    public void imprime(){  
        super.imprime();  
        System.out.println(this.salario);  
    }  
  
    public double getSalario() {  
        return salario;  
    }  
  
    public void setSalario(double salario) {  
        this.salario = salario;  
    }  
}


```


