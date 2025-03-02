---
Created: 2025-03-02
---

> [!NOTE] Uma abordagem mais simples
> Uma maneira mais simples de escrevermos nosso códigos usando Singleton

- Enum:
```
public enum AircraftSingletonEnum {  
    INSTANCE;  
    private final Set<String> cadeirasDisponiveis;  
  
  
    AircraftSingletonEnum() {  
        this.cadeirasDisponiveis = new HashSet<>();  
        this.cadeirasDisponiveis.add("1A");  
        this.cadeirasDisponiveis.add("1B");  
    }  
    public boolean compraDeCardeiras (String cadeiras) {  
        return cadeirasDisponiveis.remove(cadeiras);  
    }}
```


- Uso:
```
public class SingletonTest01 {  
    public static void main(String[] args) {  
        comprarCadeiras("1A");  
        comprarCadeiras("1A");  
    }    public static void  comprarCadeiras(String cadeiras) {  
        System.out.println(" INSTANCE (HASH CODE): " + AircraftSingletonEnum.INSTANCE.hashCode());  
        AircraftSingletonEnum instance = AircraftSingletonEnum.INSTANCE;  
        System.out.println(instance.compraDeCardeiras(cadeiras));  
    }}
```


> [!Example] Saída
```
 INSTANCE (HASH CODE): 1791741888
true
 INSTANCE (HASH CODE): 1791741888
false
```
