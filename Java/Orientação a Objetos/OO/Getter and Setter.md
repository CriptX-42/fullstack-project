---
Created: 2024-01-28
tags: []
---
#### Definição tosca
	- Para não acessar as priedades dos nossos objetos diretamente, podemos tornalos privados e internamente podemos criar Getters & Setters. Ex:
	

```
public class Pessoa {  
    private String nome;  
    private int idade;  
    private char sexo;  
  
    public  void imprime() {  
        System.out.println(this.nome);  
        System.out.println(this.idade);  
        System.out.println(this.sexo);  
    }  

	setNome(String nome){
		this.nome = nome
	}

	getNome() {
		return this.nome
	}
}
```