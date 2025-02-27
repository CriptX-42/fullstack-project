---
Created: 2025-02-27
tags:
  - Aprofundar
---

> [!NOTE] O que é?
> Um padrão criado para desacoplar as lógicas de negócios do nosso objeto


### Exemplo de uso 

- Imagine que temos a seguinte interface:

```
public interface Currency {  
    String getSymbol();  
  
}  
  
class Real implements Currency {  
    @Override  
    public String getSymbol() {  
        return "R$";  
    }  
}  
  
class UsDollar implements Currency {  
  
    @Override  
    public String getSymbol() {  
        return "$";  
    }  
}
```

- E o seguinte Enum:

```
public enum Contry {  
    BRAZIL, USA  
}
```

- Para montar isso, criamos a factory:

```
public class CurrencyFactory {  
    public static Currency newCurrency(Contry contry) {  
        switch (contry) {  
            case USA -> {  
                return new UsDollar();  
            }  
            case BRAZIL -> {  
                return new Real();  
            }  
            default -> {  
                throw new IllegalArgumentException("Não achamos a moeda");  
            }  
        }  
    }  
}
```

- O uso dela não muda muito, fica até mais simples:

```
public class FactoryTest01 {  
    public static void main(String[] args) {  
        Currency currency = CurrencyFactory.newCurrency(Contry.BRAZIL);  
        System.out.println(currency.getSymbol());  
    }  
}
```
