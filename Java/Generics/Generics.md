---
Created: 2025-02-10
tags:
  - Dicionário
---

> [!NOTE] Tudo começa com um problema
> Imagine que temos uma lista, que aceita, String, long e um objeto
> Para fazer o tratamento dessa lista saí uma logica muito verbosa
> Ex:


> [!Tips] Sumario
> 1. [[Wildcards]]



```
public static void main(String[] args) {  
    List lista = new ArrayList();  
    lista.add("teste");  
    lista.add(123L);  
    lista.add(new Consumidor("Ricardo"));  
  
    for (Object object : lista) {  
        if (object instanceof String) {  
            System.out.println(object);  
        }  
        if (object instanceof Long) {  
            System.out.println(object);  
        }  
  
        if (object instanceof Consumidor) {  
            System.out.println(object);  
        }  
  
    }  
  
}
```

- Uma lista basicamente aceita qualquer coisa, então podemos limita-lá:

```
public static void main(String[] args) {  
    List<String> lista = new ArrayList();  
    lista.add("teste");  
  
    for (String object : lista) {  
        System.out.println(object);  
    }  
}
```

> Esse check do tipo da lista é feito em tempo de compilação para retrocompatibilidade, chamamos isso de **Type erasure**
