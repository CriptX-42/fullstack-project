---
tags:
  - Construir
Creatd:
---

> [!NOTE] Definição
> A mesma das outras tantas definições, vamos obter um resultado a partir de uma operação realizada numa sequencia de elementos
> 

- Exemplo

```
public static void main(String[] args) {  
    List<Integer> integers = List.of(1,2,3,4,5,6,7,8,9);  
  
    integers.stream().reduce((x,y) -> x+y )  
            .ifPresent(System.out::println);  
  
    //Com valor inicial  
    Integer initialValueWithReduce = integers.stream()  
            .reduce(1, (x, y) -> x + y);  
    System.out.println(initialValueWithReduce);  
  
    //Uma soma mais simples  
    Integer simple = integers.stream().reduce(0, Integer::sum);  
    System.out.println(simple);  
}
```

### Exemplo pratico

- Imagine que queremos somar o valor dos jogos que são maiores do que 3 reais
- Temos dois modos de fazer

```
public class Teste08 {  
    private static List<Jogos> listaJogos = new ArrayList<>(List.of(new Jogos("GTA", 12.3),  
            new Jogos("Gran turismo", 3.55),  
            new Jogos("007 Golden Eye", 2.95),  
            new Jogos("Contra", 6.66),  
            new Jogos("DOOM", 7.11),  
            new Jogos("Medal of Honor", 1.99),  
            new Jogos("Zelda: Ocarine of the time", 1)));  
  
    public static void main(String[] args) {  
        listaJogos.stream()  
                .map(Jogos::getPrice)  
                .filter(price -> price > 3)  
                .reduce(Double::sum).ifPresent(System.out::println);  
  
        double sum = listaJogos.stream().mapToDouble(Jogos::getPrice)  
                .filter(preco -> preco > 3)  
                .sum();  
    }  
}
```