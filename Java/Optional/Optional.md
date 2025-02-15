---
Created: 2025-02-15
tags:
  - Dicionário
---

> [!NOTE] Seu objetivo
> Tentar evitar o nullPointerException. Ou ser fácil de identificar que o retorno de um método pode ser opcional
> Optional é um objeto que vai encapsular outros objetos 

### O problema

```
public class OptionalTest01 {  
    public static void main(String[] args) {  
        String name = findName("Jéssica");  
        System.out.println(name.toUpperCase());  
    }  
    private static String findName(String name) {  
        List<String> nameList = List.of("Ricardo", "Icaro");  
        int i = nameList.indexOf(name);  
        if( i != -1) { 
            return nameList.get(i);  
        }  
        return  null;  
    }  
}
```

	Imagine que temos um código onde em um método, encontramos um nome numa lista de nomes, ele pode ou não voltar com o nome, e depois de executar esse método, vamos trasnformar ele em Uppercase, sendo que o uppercase precisa de uma string. Vamos ter o seguinte erro:

![[Pasted image 20250215203151.png]]


### As 3 formas de optional

```
Optional<String> o1 = Optional.of("Ahaaa");
Optional<String> o1 = Optional.ofNullable(null);
Optional<String> o1 = Optional.empty;
```

#### Resolvendo esse problema:

```
public class OptionalTest01 {  
    public static void main(String[] args) {  
        Optional<String> name = Optional.ofNullable(findName("Jéssica"));  
        String empty = name.orElse("Não encontrou um nome");  
        System.out.println(empty);  
    }  
    private static String findName(String name) {  
        List<String> nameList = List.of("Ricardo", "Icaro");  
        int i = nameList.indexOf(name);  
        if( i != -1) {  
            return nameList.get(i);  
        }  
        return  null;  
    }  
}
```


> [!Example] Saída
```
 Não encontrou um nome
```

### Outro problema

```
public class OptionalTest01 {  
    public static void main(String[] args) {  
        Optional<String> name = Optional.ofNullable(findName("Ricardo"));  
        String empty = name.orElse("Não encontrou um nome");  
        System.out.println(name);  
    }  
    private static String findName(String name) {  
        List<String> nameList = List.of("Ricardo", "Icaro");  
        int i = nameList.indexOf(name);  
        if( i != -1) {  
            return nameList.get(i);  
        }  
        return  null;  
    }  
}
```

> Caso escolhermos para imprimir só o nome, a saída será :
> `Optional.empty`

Para resolver isso, usariamos lambda:

```
public class OptionalTest01 {  
    public static void main(String[] args) {  
        Optional<String> name = Optional.ofNullable(findName("Ricardo"));  
        String empty = name.orElse("Não encontrou um nome");  
  
        name.ifPresent(s -> System.out.println(s.toUpperCase()));  
    }  
    private static String findName(String name) {  
        List<String> nameList = List.of("Ricardo", "Icaro");  
        int i = nameList.indexOf(name);  
        if( i != -1) {  
            return nameList.get(i);  
        }  
        return  null;  
    }  
}
```


> [!Example] Saída
```
RICARDO
```


### Limpando o código

```
public class OptionalTest01 {  
    public static void main(String[] args) {  
        Optional<String> name = findName("Ricardo");  
        String empty = name.orElse("Não encontrou um nome");  
  
        name.ifPresent(s -> System.out.println(s.toUpperCase()));  
    }  
    private static Optional<String> findName(String name) {  
        List<String> nameList = List.of("Ricardo", "Icaro");  
        int i = nameList.indexOf(name);  
        if( i != -1) {  
            return Optional.of(nameList.get(i));  
        }  
        return  Optional.empty();  
    }  
}
```