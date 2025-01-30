---
Created: 2025-01-29
---


> [!NOTE] Definição
> Uma forma de todas as nossa subclasses terem acesso ao nossos atributos. Como se estivesse na nossa própria classe
> ==Porem== todas as classes no mesmo pacote vão ter acesso também (Verificar) 


- Um exemplo:

```
public class Pessoa {  
    protected String nome;  
    protected String cpf;  
    protected Endereco endereco;  
  
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


