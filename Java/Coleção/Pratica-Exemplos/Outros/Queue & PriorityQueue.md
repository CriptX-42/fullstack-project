---
Created: 2025-02-09
---

> [!NOTE] Alguns adendos
> Por padrão é FIFO
> Nossa classe adicionada a queue precisa ser obrigatoriamente um **comparable**
> O PriorityQueue serve para definir a prioridade da nossa lista com o **comparator** por exemplo


Exemplo simples: 
```
public class QueueTest01 {  
    public static void main(String[] args) {  
        Queue<String> fila = new PriorityQueue<>();  
        fila.add("D");  
        fila.add("B");  
        fila.add("A");  
        fila.add("C");  
  
        for (String s : fila) {  
            System.out.println(s);  
        }  
  
        System.out.println();  
        while (!fila.isEmpty()) {  
            System.out.println(fila.poll());  
        }  
    }  
}
```

> [!Example] Saída
```
A
C
B
D

A
B
C
D
```

