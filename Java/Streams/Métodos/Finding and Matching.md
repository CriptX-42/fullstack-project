---
Created: 2025-02-16
---
### Exemplos:

```
public static void main(String[] args) {  
    System.out.println(listaJogos.stream().anyMatch(listaJogos -> listaJogos.getPrice() > 9));  
    System.out.println(listaJogos.stream().allMatch(listaJogos -> listaJogos.getPrice() > 0));  
    System.out.println(listaJogos.stream().noneMatch(listaJogos -> listaJogos.getPrice() < 0));  
  
    listaJogos.stream().filter(listaJogos -> listaJogos.getPrice() > 3)  
            .findAny()  
            .ifPresent(System.out::println);  
      
}
```