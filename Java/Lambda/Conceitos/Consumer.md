---
Created: 2025-02-13
---

> [!NOTE] Definição
> É bem parecida com *predicate*, também é uma interface mas ela executa uma operação e não retorna nada (*void*)



```
public class LambdaTeste01 {  
    public static void main(String[] args) {  
        List<String> strings = List.of("Ricardo", "Luiz", "José");  
        forEach(strings, (String s) -> System.out.println(s));  
    }  
      
    private static <T> void forEach(List<T> list, Consumer<T> consumer) {  
        for (T e : list) {  
            consumer.accept(e);  
        }  
    }  
}
```

> consumer vai executar o código de print dentro da sua expressão, isso está definido no consumer.aceept, passando o elemento como parametro


> [!Example] Saída
```
Ricardo
Luiz
José 
```
