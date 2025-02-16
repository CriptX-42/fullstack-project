---
Created: 2025-02-16
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