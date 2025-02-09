---
Created: 2025-02-09
---

> [!NOTE] Alguns adendos
> A mesma coisa do Map, trabalha com chave e valor e uma mistura do navegable
> Ainda precisamos passar um comparator ou comparable para a **chave**
> A ordenação vai ser feita pela **Chave**


Uso:
```
public static void main(String[] args) {  
    NavigableMap<String, String> map = new TreeMap<>();  
    map.put("A", "Letra A");  
    map.put("D", "Letra D");  
    map.put("C", "Letra C");  
    map.put("B", "Letra B");  
  
    for (Map.Entry<String, String> entry : map.entrySet()) {  
        System.out.println(entry.getKey()  + " " + entry.getValue());  
    }  
      
}
```


> [!Example] Saída
```
A Letra A
B Letra B
C Letra C
D Letra D
```


Também temos os métodos para o NavegableMap:

**Ceiling**
**higher**
**lower**
**floor**