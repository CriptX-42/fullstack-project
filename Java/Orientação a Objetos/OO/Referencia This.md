---
Created: 2025-01-28
tags: []
---
#### Exemplo de classes usando 'this'

```
public class Pessoa {  
    public String nome;  
    public int idade;  
    public char sexo;  
  
    public  void imprime() {  
        System.out.println(this.nome);  
        System.out.println(this.idade);  
        System.out.println(this.sexo);  
    }  
}
```

	Uso da classe pessoa

```
public static void main(String[] args){  
    Pessoa pessoa = new Pessoa();  
    pessoa.nome = "Ricardo";  
    pessoa.idade = 27;  
    pessoa.sexo = 'M';  
  
    pessoa.imprime();  
  
}

Saída: 

Ricardo
27
M
```
