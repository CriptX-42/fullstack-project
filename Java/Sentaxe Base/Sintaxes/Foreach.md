---
Created: 2025-01-28
tags:
---
### Anatomia
```
public static void main(String[] args){  
    for(Tipo [variavel]: arrayOuColeção)
}
```


#### Exemplo


```
   public static void main(String[] args){  
        int[] idades = new int[]{1,2,3,4,5};  
  
        for(int idade: idades) {  
            System.out.println(idade);  
        }  
    }
    Sysout: 
    1
	2
	3
	4
	5
```

#### Uso
	Não temos como acessar um index especifico
	É mais simples


#### Uso com [[Array Multi]]

```
int [][] dias = new int[3][3];  
  
        dias[0][0] = 31;  
        dias[0][1] = 28;  
        dias[0][2] = 31;  
  
        dias[1][0] = 31;  
        dias[1][1] = 28;  
        dias[1][2] = 31;  
  
  
        for (int[] base: dias) {  
            for (int num: base){  
                System.out.println(num);  
            }  
        }  
    }

Sysout: 
31
28
31

31
28
31

0
0
0
```