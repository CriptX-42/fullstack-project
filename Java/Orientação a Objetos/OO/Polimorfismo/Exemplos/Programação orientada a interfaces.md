---
Created: 2025-01-31
---

> [!NOTE] Definição rápida
> Consiste em instanciar meu objeto mais especifico usando o tipo da  minha interface mais genérica

Imagine a seguinte implementação: 
![[Java/Orientação a Objetos/OO/Polimorfismo/Exemplos/Untitled Diagram.svg]]

> Para instanciar os serviços de uma forma genérica, podemos usar nossa interface como orientação. Ex:

- Repositório (interface):
```java
public interface Repositorio {  
    void salvar();  
}
```


- Serviço:
```java
public class RepositorioArquivo implements Repositorio {  
    @Override  
    public void salvar() {  
        System.out.println("Savando arquivo");  
    }  
}
```


```java
public class RepositorioBancoDeDados implements Repositorio {  
    @Override  
    public void salvar() {  
        System.out.println("Savando no BD");  
    }  
}
```


```java
public class RepositorioMemoria implements Repositorio {  
    @Override  
    public void salvar() {  
        System.out.println("Savando em memória");  
    }  
}
```


- Implementação genérica:

```java
public static void main(String[] args) {  
    Repositorio repo1 = new RepositorioArquivo();  
    Repositorio repo2 = new RepositorioMemoria();  
    Repositorio repo3 = new RepositorioArquivo();  
    repo1.salvar();  
}
```