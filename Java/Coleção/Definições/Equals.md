---
Created: 2025-02-02
tags:
  - Duvidas
---
Vamos a um simples exemplo:

```
public static void main(String[] args) {  
    Smartphone s1 = new Smartphone("123", "Samsung");  
    Smartphone s2 = new Smartphone("123", "Samsung");  
  
    System.out.println(s1.equals(s2));  

Saída: 
------------------------------
false
}
```

Pois o equals não está na mesma variavel de referencia de S1 como comparador


#### Comparando objetos com a sobrescrita do **equals**

	Para a sobrescrita temos o seguintes requisitos:
	
		*Reflexivo* : x.equals(x) tem que ser true para tudo que for diferente de null
		
		*Simetrico* : para x e y diferentes de null, se x.equals(y) == true, y.equals(x) == true
		
		*Transitividade* : para x,y,z diferentes de null, se x.equals(y) == true, e x.equals(z) == true, logo y.equals(z) == true
		
		*Consistencia* : x.equals(x) sempre retorna true se x for diferente de null
		Para x diferente de null, x.euqlas(null) tem que retornar false

```
public class Smartphone {  
    private String serialNumber;  
    private String marca;  
  
    public Smartphone(String serialNumber, String marca) {  
        this.serialNumber = serialNumber;  
        this.marca = marca;  
    }  
  
    @Override  
    public boolean equals(Object obj) {  
        if(obj == null) return false;  
        if(this == obj) return true;  
        if(this.getClass() != obj.getClass()) return  false;  
        Smartphone smartphone = (Smartphone) obj;  
        return serialNumber != null && serialNumber.equals(smartphone.serialNumber);  
    }  
  
 Saída: 
 --------------------
 True
}
```



> [!Warning] Duvida
> Fazemos um cast de smartphone ` Smartphone smartphone = (Smartphone) obj;`
