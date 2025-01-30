---
Created: 2025-01-29
tags:
  - Aprofundar
---
### O que é
- Uma propriedade executada antes do construtor

> [!NOTE] Prioridade de inicialização
>  0. Bloco de inicialização é executado quando a JVM carregar classe
>  1. Alocado espaço em memória pro objeto
>  2. Cada atributo de classe é criado e inicializado com valores default ou que for passado
>  3. Bloco de inicialização é executado
>  4. Construtor é executado
#### Exemplo
```
public class Pessoa {  
    public String nome;  
    public int idade;  
    public char sexo;  
    
  //Bloco de inicialização
   {
   }
   ...
}
```

#### Bloco de inicialização com [[Modificador Static]]
- Só acessa atributos estáticos e não acessa atributos de instancia 
- Ele não vai ser executado todas as vezes que o objeto for criado
```
public class Pessoa {  
    public String nome;  
    public int idade;  
    public char sexo;  
    
  //Bloco de inicialização
   static {
   }
   ...
}
```
