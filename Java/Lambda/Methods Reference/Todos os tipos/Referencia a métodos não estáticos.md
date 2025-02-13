---
Created: 2025-02-13
---

> [!NOTE] Definição
> Nada muda, só vamos precisar de um objeto para referenciar um método, pois ele não é **estático**

- Classe de serviço (com método não estatico):

```
public class JogosComparator {  
  
    public int compareByTitleNonStatic(Jogos a1, Jogos a2) {  
        return a1.getTitle().compareTo(a2.getTitle());  
    }  
}
```

- Classe de uso
```
public class MethodsReferenceTest02 {  
    public static void main(String[] args) {  
        JogosComparator jogosComparator = new JogosComparator();  
        List<Jogos> jogos = new ArrayList<>(List.of(new Jogos("GTA", 1),  
                new Jogos("Red Dead", 3),  
                new Jogos("it take two", 6)));  
        jogos.sort(jogosComparator::compareByTitleNonStatic);  
        System.out.println(jogos);  
    }  
}
```

> Nota que estamos estanciando `JogosComparator jogosComparator = new JogosComparator();` e usando normalmente no nosso Reference


### O terceiro tipo
Um modo de referenciar a classe dentro do reference (dificil pra de entender isso)

Um exemplo:
```
public static void main(String[] args) {  
    JogosComparator jogosComparator = new JogosComparator();  
    List<String> strings = new ArrayList<>(List.of("Ricardo", "Carvalho"));  
    strings.sort(String::compareTo);  
    System.out.println(strings);  
}
```

> String implementa o compareTo, por isso podemos referenciar dentro de sort


> [!Example] Saída
```
[Carvalho, Ricardo]
```
