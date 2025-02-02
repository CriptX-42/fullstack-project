---
Created: 2025-02-02
---

> [!NOTE] Primeiramente
> Strings em java são imutáveis 


```
String nome = "Ricardo"; // String constant poll
``` 
![[Java/img/Untitled Diagram 1.svg]]

> [!Warning] O motivo do equals
> Por isso usamos o equals, se tivermos mais uma variavel String, e ela for igual a nossa primeira variavel, gostaríamos de saber se faz referencia ao mesmo objeto

```
public class StringTest01 {  
    public static void main(String[] args) {  
        String eu = "Ricardo";  
        String eu2 = new String("Ricardo");  
          
        System.out.println(eu == eu2);  
        System.out.println(eu == eu2.intern());  
        System.out.println(eu.equals(eu2));  

	Saída:
	---------------------
	false
	true
	true
  
    }  
}
```


#### Melhoria de performance

Vamos a um pequeno problema de performance no incremento de uma string:

```
public class StringTest01 {  
    public static void main(String[] args) {  
        long inicio = System.currentTimeMillis();  
        stringPerformanceTest(100_000); // _ pode ser usado com separador em java  
        long fim = System.currentTimeMillis();  
        System.out.println("tempo gasto " + (fim-inicio) + " ms");  
    }  
  
    private static void stringPerformanceTest (int tamanho)  {  
        String texo = "";  
        for (int i = 0; i < tamanho; i++) {  
            texo += i;  
        }  
    }  

	Saída
	--------------
	tempo gasto 3526 ms
}
```

- Resolvendo com [[String Builder]]:

```
public class StringTest01 {  
    public static void main(String[] args) {  
        long inicio = System.currentTimeMillis();  
        stringPerformanceTest(100_000); // _ pode ser usado com separador em java  
        long fim = System.currentTimeMillis();  
        System.out.println("tempo gasto " + (fim-inicio) + " ms");  
    }  
  
    private static void stringPerformanceTest (int tamanho)  {  
        StringBuilder sb = new StringBuilder(tamanho);  
        for (int i = 0; i < tamanho; i++) {  
            sb.append(i); // acrescentar i  
        }  
    }  

	Saída:
	-----------------
	tempo gasto 12 ms
}
```

- Resolvendo com String Buffer:
```
public class StringTest01 {  
	    public static void main(String[] args) {  
	    long inicio = System.currentTimeMillis();  
	    stringPerformanceTest(100_000); // _ pode ser usado com separador em java  
	    long fim = System.currentTimeMillis();  
	    System.out.println("tempo gasto " + (fim-inicio) + " ms");  
	}  
	  
	private static void stringPerformanceTest (int tamanho)  {  
	    StringBuffer sb = new StringBuffer(tamanho);  
	    for (int i = 0; i < tamanho; i++) {  
	        sb.append(i); // acrescentar i  
	    }  
	} 

	Saída:
	-----------------
	tempo gasto 15 ms
}
```