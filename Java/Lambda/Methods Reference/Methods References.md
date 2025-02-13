---
Created: 2025-02-13
tags:
  - Dicionário
---

> [!NOTE] Regra
> Se nosso lambda chama apenas um método, ele pode utilizar Methods Reference


> [!Tip] Sumário de Methods Reference
> 1. [[Metodos Estaticos]]
> 2. [[Referencia a métodos não estáticos]]
> 3. [[Referencia para construtor]]


> Por isso nosso intellij está nos apontado esse alerta:
> ![[Pasted image 20250213190735.png]]
> E assim ficaria com a aplicação do methods reference:

```
public class LambdaTeste02 {  
    public static void main(String[] args) {  
        List<String> strings = List.of("Ricardo", "Carvalho");  
        List<Integer> integers = map(strings, String::length);  
        System.out.println(integers);  
    }  
  
    private static <T, R> List<R> map(List<T> list, Function<T, R> function) {  
        List<R> result = new ArrayList<>();  
        for (T e: list) {  
            R r = function.apply(e);  
            result.add(r);  
        }  
        return  result;  
    }  
}
```

### Ler mais em:

[Documentação da oracle](https://docs.oracle.com/javase/tutorial/java/javaOO/methodreferences.html) 


