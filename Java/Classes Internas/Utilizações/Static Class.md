---
Created: 2025-02-11
---

> [!NOTE] Definição
> É uma outra classe de auto nível dentro da nossa classe (que já é de auto nível)

Exemplo de uso:

```
public class OuterClasses03 {  
    private String name = "Ricardo";  
    static class Nested {  
        void print() {  
            System.out.println(new OuterClasses03().name);  
        }  
    }  
    public static void main(String[] args) {  
        Nested nested = new Nested();  
        nested.print();  
    }  
}
```