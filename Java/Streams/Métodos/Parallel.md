---
Created: 2025-02-20
---

> [!NOTE] Uma breve definição
> Nada mais é do que um stream com processamento paralelo 

### Comparando performance

```
public static void main(String[] args) {  
  
    System.out.println(Runtime.getRuntime().availableProcessors());  
    long num = 10_000_000;  
  
    sumFor(num);  
    sumStreamIterate(num);  
    sumStreamParallel(num);  
    sumLongStream(num);  
    sumLongStreamParallel(num);  
}
```

```
private static void sumFor(long num) {  
    System.out.println("Sum for" );  
    long result = 0;  
    long init = System.currentTimeMillis();  
    for (int i = 0; i < num; i++) {  
        result += i;  
    }  
    long end = System.currentTimeMillis();  
    System.out.println(result + " " + (end - init) + "ms");  
  
}  
  
private static void sumStreamIterate(long num) {  
    System.out.println("Sum Stream" );  
    long init = System.currentTimeMillis();  
    long result = Stream.iterate(1L, i-> i + 1).limit(num).reduce(0L, Long::sum);  
    long end = System.currentTimeMillis();  
    System.out.println(result + " " + (end - init) + "ms");  
  
}  
  
private static void sumStreamParallel(long num) {  
    System.out.println("Sum Stream parallel" );  
    long init = System.currentTimeMillis();  
    long result = Stream.iterate(1L, i-> i + 1).limit(num).parallel().reduce(0L, Long::sum);  
    long end = System.currentTimeMillis();  
    System.out.println(result + " " + (end - init) + "ms");  
  
}  
  
private static void sumLongStream(long num) {  
    System.out.println("Sum LongStream" );  
    long init = System.currentTimeMillis();  
    long result = LongStream.rangeClosed(1L, num).reduce(0L, Long::sum);  
    long end = System.currentTimeMillis();  
    System.out.println(result + " " + (end - init) + "ms");  
  
}  
  
private static void sumLongStreamParallel(long num) {  
    System.out.println("Sum LongStream Parallel" );  
    long init = System.currentTimeMillis();  
    long result = LongStream.rangeClosed(1L, num).parallel().reduce(0L, Long::sum);  
    long end = System.currentTimeMillis();  
    System.out.println(result + " " + (end - init) + "ms");  
  
}
```


> [!Example] Saída
```
Sum for
49999995000000 13ms

Sum Stream
50000005000000 287ms

Sum Stream parallel
50000005000000 826ms

Sum LongStream
50000005000000 29ms

Sum LongStream Parallel
50000005000000 43ms
```
