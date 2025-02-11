---
Created: 2025-02-11
tags:
  - Duvidas
---

> [!NOTE] O que são?
> Classes que vão existir brevemente no código e não podem ser utilizadas em nenhum outro lugar

Exemplo: 

```
class Animal {  
    public void walk() {  
        System.out.println("animal walking");  
    }  
}  
public class AnonymousClassesTest01 {  
    public static void main(String[] args) {  
        Animal animal = new Animal(){  
            // Isso é uma subclasse de animal  
  
            @Override  
            public void walk() {  
                System.out.println("Animal stoping");  
            }  
        };  
        animal.walk();  
    }  
}
```

Estamos sobrescrevendo o método walk dentro da sua classe, utilizando uma subclasse.
