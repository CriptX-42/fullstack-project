---
Created: 2025-01-28
---
#### Definição
- Independente do nosso objeto ter ou não um construtor aparente. Sempre estamos construindo algo (um objeto).
- É o inicializador de um objeto
- Um construtor força a inserção de dados no nosso objeto. Ex:

```
public class Pessoa {  
    private String nome;  
    private int idade;  
    private char sexo;  
  
    public Pessoa(String nome){
	    this.nome = nome
    }
...
	
}
```

Uso

```
public static void main(String[] args){  
    Pessoa pessoa = new Pessoa("Ricardo");  
   ...
  
}


```


#### Sobrecarga

```
public class Pessoa {  
    private String nome;  
    private int idade;  
    private char sexo;  
  
	public Pessoa(){
	}

	public Pessoa(String nome){
		this(); // chamou o primeiro construtor, e podemos passar parametros aí
	    this.nome = nome
    }

...
	
}
```

Se for chamar outro construtor. ==Obrigatoriamente deve ser a primeira linha do construtor== 
#### Regras
- Não tem nenhum retorno
- Criamos usando um modificador seguido do ==nome da classe== 
- Se não construímos um construtor na classe. O java vai adicionar no meio da compilação
- Ele é executado antes de qualquer método da nossa classe
- Podemos fazer [[Sobrecarga]] de construtores