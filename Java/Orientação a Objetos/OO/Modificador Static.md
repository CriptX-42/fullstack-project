---
Created: 2025-01-29
tags:
  - Duvidas
---

- Uma forma de atribuir um valor a um atributo e não deixar ele ser modificado por setters ou nada do tipo

```
public class Carro {  
    public String marca;
    public static double velocidadeMaxima = 250; // vai ser padrão para todas as instancias desse objeto, e não vai ser modificado  
  ...
}
```


> [!NOTE] Como alterar mesmo assim
> Só conseguimos alterar caso chamemos a classe diretamente e nosso atributo for ´public´

```
public static void main(String[] args) {
	Carro.velocidadeMaxima = 180;
}
```

Ou também alterando pelos modificadores

```
public class Carro {  
    public String marca;
    private static double velocidadeMaxima = 250; 

	public static setVelocidadeLimite(double velocidadeMaxima) {
		Carro.velocidadeMaxima = velocidadeMaxima; 
	}

	public static setVelocidadeLimite(double velocidade) {
		// como não tem o mesmo nome de inferencia, não precisamos colocar 'Carro'...
		return velocidadeMaxima 
	}

}
```


> [!NOTE] Bloco de inicialização estatico
> [[Java/Orientação a Objetos/OO/Bloco de inicialização]] com modificadores estaticos
