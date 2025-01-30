---
Created: 2025-01-30
---


> [!NOTE] Definição
> Uma classe abstrata é uma classe que não pode ser instanciada, serve de template/modelo a outras classes. ela pode conter métodos com implementação completa e também implementações abstratas


> [!NOTE] Regras
> 1. Uma classe abstrata não pode ser instanciada
> 2. Uma classe abstrata foi criada para ser estendida, foi criada para ser uma superclasse
> 3. Podem existir métodos **Abstratos** ou **Completos** dentro de uma classe abstrata
 

### Mão na massa

	Vamos criar uma classe template chamada funcionario:
	
```
public abstract class Funcionario {  
    protected String nome;  
    protected double salario;  
  
    public Funcionario(String nome, double salario) {  
        this.nome = nome;  
        this.salario = salario;  
    }  
}
```

	Essa classe pode implementar agora quantos tipos de funcionarios existir na minha empresa. Vai servir de template para o gerente ou até mesmo desenvolvedor, qualquer um dos meus funcionarios:

```
public class Gerente extends Funcionario {  
    public Gerente(String nome, double salario) {  
        super(nome, salario);  
    }  
  
    @Override  
    public String toString() {  
        return "Gerente{" +  
                "nome='" + nome + '\'' +  
                ", salario=" + salario +  
                '}';  
    }  
}
```

Exemplo de uso e saída:

```
public static void main (String[] args) {  
    Gerente gerente = new Gerente("Ricardo", 2000);  
  
    System.out.println(gerente.toString());  
  
}

Saída:
// Gerente{nome='Ricardo', salario=2000.0}
```