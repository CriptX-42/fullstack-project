---
Created: 2025-02-13
tags:
---

> [!NOTE] Definição
> Uma interface do pacote Fucional, e recebe duas coisas <T, R>. 
> O T é oque vamos receber
> O R é o que vamos retornar
> E podemos fazer qualquer coisa com isso

- Uso:
```
public class LambdaTeste02 {  
    public static void main(String[] args) {  
        List<String> strings = List.of("Ricardo", "Carvalho");  
        List<Integer> integers = map(strings, (String s) -> s.length());  
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



> [!Example] Saída
```
[7, 8]
```
