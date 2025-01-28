---
Created: 2025-01-28
tags:
---
### Anatomia
```
public static void main(String[] args){  
    int[] idades = new int[3];  
  
    idades[2] = 11;  
    System.out.println(idades[2]); //11 
}
```

#### Integrado a valores
```
public static void main(String[] args){  
    int[] idades = {1,2,3,4,5};  
  
    for (int i = 0; i < idades.length; i++) {  
        System.out.println(idades[i]);  
    }  
  
}

Sysout: 
1
2
3
4
5
```

```
public static void main(String[] args){  
    int[] idades = new int[]{1,2,3,4,5};  
  
    for (int i = 0; i < idades.length; i++) {  
        System.out.println(idades[i]);  
    }  
  
}

Sysout: 
1
2
3
4
5
```
