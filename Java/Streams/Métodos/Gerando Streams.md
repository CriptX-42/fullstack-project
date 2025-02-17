---
Created: 2025-02-17
---
Vamos tentar trabalhar com Streams de forma independente:

```
public class Teste09 {  
    public static void main(String[] args) {  
        IntStream.range(1,50).filter(n -> n % 2 ==0).forEach(n -> System.out.print(n + " "));  
        System.out.println();  
        IntStream.rangeClosed(1,50).filter(n -> n % 2 ==0).forEach(n -> System.out.print(n + " " ));  
  
        System.out.println();  
        Stream.of("Oi", "Eu", "Sou", "Ricardo")  
                .map(String::toUpperCase)  
                .forEach(s -> System.out.print(s + " "));  
  
          
    }  
}
```


> [!Example] 
```
2 4 6 8 10 12 14 16 18 20 22 24 26 28 30 32 34 36 38 40 42 44 46 48 
2 4 6 8 10 12 14 16 18 20 22 24 26 28 30 32 34 36 38 40 42 44 46 48 50 
OI EU SOU RICARDO
```
