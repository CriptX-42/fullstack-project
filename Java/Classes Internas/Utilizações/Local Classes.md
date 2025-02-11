---
Created: 2025-02-11
---

> [!NOTE] O que é
> Quando você tem uma classe dentro de um método
> 
> Eu nunca vi isso!
> Eu nunca usei isso! 
> Não conheço ninguém que use isso! 

Uso:

```
public class OuterClassesTeste02 {  
    private String nome = "Nissan";  
    void  print() {  
        class LocalClass {  
            public void printLocal() {  
                System.out.println(nome);  
            }  
        }  
        LocalClass localClass = new LocalClass();// cria um atributo  
        localClass.printLocal();  
    }  
    public static void main(String[] args) {  
        OuterClassesTeste02 outer = new OuterClassesTeste02();  
        outer.print();  
    }  
}
```