---
Created: 2025-02-16
tags:
  - Duvidas
---


> [!Note] O que faz?
> A mesma coisa do map mas funciona com propriedades aninhadas (uma lista de lista por exemplo)
> Ele retira coleção/atributo de uma lista aninhada


### Modo sem FlatMap

```
public static void main(String[] args) {  
    List<List<String>> faculdade = new ArrayList<>();  
    List<String> cursoProgramacao = List.of("Ricardo", "Lucas Almeida", "Rafael Oliveira", "Fernanda Lima");  
    List<String> cursoEngenharia = List.of("Bruno Nogueira", "Amanda Silveira", "Juliana Rocha", "Eduardo Martins");  
    List<String> cursoMatematica = List.of("Thiago Moreira", "Vanessa Carvalho", "Felipe Andrade", "Larissa Souza");  
  
    faculdade.add(cursoProgramacao);  
    faculdade.add(cursoEngenharia);  
    faculdade.add(cursoMatematica);  
  
    for (List<String> pessoas : faculdade) {  
        for (String pessoa : pessoas) {  
            System.out.println(pessoa);  
        }  
  
    }  
  
}
```


### Com FlatMap

```
public static void main(String[] args) {  
    List<List<String>> faculdade = new ArrayList<>();  
    List<String> cursoProgramacao = List.of("Ricardo", "Lucas Almeida", "Rafael Oliveira", "Fernanda Lima");  
    List<String> cursoEngenharia = List.of("Bruno Nogueira", "Amanda Silveira", "Juliana Rocha", "Eduardo Martins");  
    List<String> cursoMatematica = List.of("Thiago Moreira", "Vanessa Carvalho", "Felipe Andrade", "Larissa Souza");  
  
    faculdade.add(cursoProgramacao);  
    faculdade.add(cursoEngenharia);  
    faculdade.add(cursoMatematica);  
  
    faculdade.stream().flatMap(Collection::stream).forEach(System.out::println);  
  
}
```


> [!Danger] Duvida
> Consultar: https://www.youtube.com/watch?v=wCEEhV4Hkio&list=PL62G310vn6nFIsOCC0H-C2infYgwm8SWW&index=208
