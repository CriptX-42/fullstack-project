---
Created: 2025-02-11
tags:
  - Dicionário
---

> [!NOTE] Definição
> É basicamente uma classe dentro da outra
> Sem trabalhar com **interfaces graficas**, é mais complicado de trabalhar com Inner Class


> [!Tip] Sumário
> 1. [[Local Classes]]


Uso:

```
public class OuterClassesTest01 {  
    private String name = "Monkey";  
  
    class Inner {  
        public void printerOuterClassAttribute() {  
            System.out.println(name);  
            System.out.println(this);  
            System.out.println(OuterClassesTest01.this);  
        }  
    }  
    public static void main(String[] args) {  
        //Outer Class  
        OuterClassesTest01 outerClass = new OuterClassesTest01();  
        Inner inner = outerClass.new Inner();  
        inner.printerOuterClassAttribute();  
    }  
}
```


> [!Example] Saída
```
Monkey
ZZAclassesInternasTeste.OuterClassesTest01$Inner@15aeb7ab
ZZAclassesInternasTeste.OuterClassesTest01@7b23ec81 
```

- O This referencia a classe que se apresenta
- Para existir uma InnerClass, precisa existir uma OuterClass