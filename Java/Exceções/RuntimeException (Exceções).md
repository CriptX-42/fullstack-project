---
Created: 2025-01-31
---



> Exemplo de RuntimeException

```
public class Test {  
    public static void main(String[] args) {  
        Object object = null;  
        System.out.println(object.toString());  
    }  
}
```


> [!Error] Saída
> Exception in thread "main" java.lang.**NullPointerException**: Cannot invoke "Object.toString()" because "object" is null
at OException.Runtime.Test.main(Test.java:6)

#### Para facilitar a consulta de exceptions

[Documentação de Runtime da oracle](https://docs.oracle.com/javase/8/docs/api/java/lang/RuntimeException.html)


#### Utilizando o throw new

```
public class Test {  
    public static void main(String[] args) {  
        System.out.println(divisao(1, 0));  
    }  
  
    private static int divisao(int a, int b) {  
        if(b == 0){  
            throw new IllegalArgumentException("Não pode fazer divisão por 0");  
        }  
        return a/b;  
    }  
}
```


> [!Error] Saída
> Exception in thread "main" java.lang.IllegalArgumentException: Não pode fazer divisão por 0
at OException.Runtime.Test.divisao(Test.java:10)
at OException.Runtime.Test.main(Test.java:5)
