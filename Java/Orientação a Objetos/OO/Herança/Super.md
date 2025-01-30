---
Created: 2025-01-29
---


> [!NOTE] Definição
> Quando temos um objeto mais especifico e precisamos abstrair uma ação do objeto menos especifico (a objeto pai). Podemos usar o  **super** como uma forma de não sobrescrever e sim aproveitar as ações da classe pai.



- Um exemplo:

```
public class Pessoa {  
    public String nome;  
    public String cpf;  
    private Endereco endereco;  
  
    // A ação de imprimir é apenas da classe pessoa
    public void imprime() {  
        System.out.println(this.nome);  
        System.out.println(this.nome);  
    }  
      
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


E se utilizarmos na classe filho o **imprime()**. Nosso compilador logo diz que ele vai sobrescrever o que existe me *Pessoa*:

![[Pasted image 20250129150007.png]]

- Mas caso nós adicionarmos o **super** a nossa função **imprime()**. Conseguimos acessar a ação da classe pai (*Pessoa*) e ainda executar uma ação mais especifica em *Funcionário*:

```
public class Funcionario extends Pessoa {  
    public double salario;  
  
  
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