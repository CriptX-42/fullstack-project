---
Created: 2025-01-30
---

> [!NOTE] Uma breve descrição...
> "É muito parecido com classe abstrata. Mas interface é interface e classe é classe" - Vozes da minha cabeça
> 
>  Servem como contrato, ou seja é uma referência que diz o que a classe **deve implementar**
>  
>Todos os métodos dentro da interface tem a característica de ser **public e abstract** de uma forma *velada*
>
>Nós não usamos o **extends** para implementar um abstrato, usamos o **implements**

> [!NOTE] Algumas definições
> **Interface funcional:** Apenas um método abstrato


	Exemplo:

```
public interface DataLoader {  
    void load();  
}
```

	Adicionando ao nosso objeto:
	
```
public class DatabaseLoader implements DataLoader {  
  
    @Override  
    public void load() {  
        System.out.println("Carregando dados do banco");  
    }  
}
```


> [!NOTE] Mais regras
> Podemos implementar quantas interfaces quisermos na nossa classe
> 
> ==E não podemos instanciar uma interface==. (verificar)
> 

#### Implementação default

	Para não obrigar uma classe a implementar um novo método abstrato de uma interface, podemos implementar métodos concretos a nossa interface.
	Isso possibilitou o java a atualizar interfaces que já estavam em uso sem qubrar o que todos já estavam usando. Ex:

```
public interface DataLoader {  
    void load();  

	default void checkPermission() {
		Sysout("Fazendo checagem de permissões")
	}
}
```

> Agora não precisamos implementar o método **checkPermission** em classes filhas ao *DataLoader*. A implementação se torna velada e opcional


#### Atributos e métodos estáticos
[[Atributos e métodos estáticos]]

#### Atribuindo uma interface funcional


- Não podemos adicionar um método além do **test**
```
@FunctionalInterface  
public interface CarPredicate {  
    boolean test(Car car);  
}
```