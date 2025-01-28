---
Created: 2025-01-28
---
- Podemos simplificar todos esses sets na nossa classe para incluir valores:

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
...
}
```

- Desse modo:

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

	
	public void init(String nome, int idade) {
		this.nome = nome;
		this.idade = idade;
	}
	
	//Sobrecarga
	// E podemos criar quantos métodos quiser, incluindo outros objetos
	public void init(String nome, int idade, char sexo) {
		this.nome = nome;
		this.idade = idade;
		this.sexo = sexo;
	}
	
	setNome(String nome){
			this.nome = nome;
		}

	getNome() {
		return this.nome;
	}
	...
}
```

#### E podemos simplificar ainda mais:

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

	
	public void init(String nome, int idade) {
		this.nome = nome;
		this.idade = idade;
	}
	
	//Sobrecarga
	// E podemos criar quantos métodos quiser, incluindo outros objetos
	public void init(String nome, int idade, char sexo) {
		this.init(nome, idade);
		this.sexo = sexo;
	}
	
	setNome(String nome){
			this.nome = nome;
		}

	getNome() {
		return this.nome;
	}
	...
}
```