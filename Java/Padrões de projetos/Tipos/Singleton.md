---
Created: 2025-03-01
tags:
  - Aprofundar
---

> [!NOTE] No que consiste o padrão?
> Imagine que temos uma classe com apenas um objeto, e esse objeto deve ser acessível a qualquer lugar do nosso projeto. É muito comum o uso de singleton em drivers de conexão com o banco.

### Um exemplo Eager (Aprofundar)

- Imagine que temos a seguinte classe:

```
public class Aircraft {  
    private final Set<String> cadeirasDisponiveis = new HashSet<>();  
    private String name;  
  
    public Aircraft(String name) {  
        this.name = name;  
    }  
  
    {  
        cadeirasDisponiveis.add("1A");  
        cadeirasDisponiveis.add("1B");  
    }  
  
    public boolean compraDeCardeiras (String cadeiras) {  
        return cadeirasDisponiveis.remove(cadeiras);  
    }  
}
```

Quando tentarmos comprar uma cadeira, e essa compra se repetir, isso vamos ter como resultado:

```
public class AircraftTest01 {  
    public static void main(String[] args) {  
  
        comprarCadeiras("1A");  
        comprarCadeiras("1A");  
    }  
  
    public static void  comprarCadeiras(String cadeiras) {  
        Aircraft aircraft = new Aircraft("787");  
        System.out.println(aircraft.compraDeCardeiras(cadeiras));  
    }  
}
```


> [!Example] Saída
```
true
true
```

- Isso acontece pois temos dois objetos alocados em diferentes em nossas memórias. Mas existe uma forma de fazer isso de maneira unica 

### Usando Eager 

- Estamos instanciando sempre o mesmo 797
```
public class AircraftSingletonEager {  
    //Eager Initialization  
    private static final AircraftSingletonEager INSTANCE = new AircraftSingletonEager("787");  
    private final Set<String> cadeirasDisponiveis = new HashSet<>();  
    private String name;  
  
    private AircraftSingletonEager(String name) {  
        this.name = name;  
    }  
  
    {  
        cadeirasDisponiveis.add("1A");  
        cadeirasDisponiveis.add("1B");  
    }  
  
    public boolean compraDeCardeiras (String cadeiras) {  
        return cadeirasDisponiveis.remove(cadeiras);  
    }  
  
    public static AircraftSingletonEager getInstance() {  
        return INSTANCE;  
    }  
}
```

- Agora por causa da maneira como criamos o objeto, não precisamos instanciar com **new**
```
public class AircraftTest01 {  
    public static void main(String[] args) {  
  
        comprarCadeiras("1A");  
        comprarCadeiras("1A");  
    }  
  
    public static void  comprarCadeiras(String cadeiras) {  
        AircraftSingletonEager instance = AircraftSingletonEager.getInstance();  
        System.out.println(instance.compraDeCardeiras(cadeiras));  
    }  
}
```

> [!Example] Saída
```
true
false
```
