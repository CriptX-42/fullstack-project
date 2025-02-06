---
Created: 2025-02-06
tags:
  - Duvidas
---
#### Conversão de uma lista para um Array

```
public static void main(String[] args) {  
    List<Integer> lista = new ArrayList<>();  
    lista.add(1);  
    lista.add(2);  
    lista.add(3);  
  
    lista.toArray(new Integer[0]);  
  
    System.out.println(lista);  
}
```


> [!Warning] Um adendo
> Se utilizarmos 0 no `lista.toArray(new Integer[0]);` o java vai descobrir o tamanho do array


> [!Example] Saída
```
[1, 2, 3]
```


#### Convertendo Array em Lista com **AsList**

```
public static void main(String[] args) {  
  
    Integer[] numerosArray = new Integer[3];  
    numerosArray[0] = 42;  
    numerosArray[1] = 24;  
    numerosArray[2] = 1;  
  
    List<Integer> list = Arrays.asList(numerosArray);  
    System.out.println(Arrays.toString(numerosArray));  
    System.out.println(list);  
  
}
```


> [!Example] Saída
```
[42, 24, 1]
[42, 24, 1]
```


> [!Warning] Alguns cuidados
> Se nós mudarmos um valor no na lista convertida `list.set(0, 12);`
> Ele vai mudar o primeiro array para 12, tanto do convertido quanto do original, pois cria um link com array original


##### Resolvendo esse problema

Pesquisar mais sobre
