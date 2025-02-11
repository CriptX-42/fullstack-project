---
Created: 2025-02-11
---

> [!Warning] Anatomia
> `private static <T> void criarArrayComUmObjeto(T t)`  o generico vem sempre depois do modificador de acesso e antes do retorno do método 

- Exemplo de uso:

```
public class MetodosGenericosTeste01 {  
    public static void main(String[] args) {  
        criarArrayComUmObjeto(new Barco("Canoa quebrada"));  
    }  
    private static <T> void criarArrayComUmObjeto(T t) {  
        List<T> list = List.of(t);  
        System.out.println(list);  
    }  
}
```