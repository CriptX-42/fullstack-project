---
Created: 2025-02-13
---
- Imagine que temos esse código:
```
public class MethodsReferenceTeste01 {  
    public static void main(String[] args) {  
        List<Jogos> jogos = new ArrayList<>(List.of(new Jogos("GTA", 1),  
                new Jogos("Red Dead", 3),  
                new Jogos("it take two", 6)));  
        Collections.sort(jogos, (a1, a2) -> a1.getTitle().compareTo(a2.getTitle()));  
        System.out.println(jogos);  
    }  
}
```

Dentro do compare estamos passando `(a1, a2) -> a1.getTitle().compareTo(a2.getTitle()));`
Conseguimos simplificar isso usando Methods Reference. Dessa forma:

- Classe de serviço:
```
public class JogosComparator {  
    public static int compareByTitle(Jogos a1, Jogos a2) {  
        return a1.getTitle().compareTo(a2.getTitle());  
    }  
}
```

- Classe de teste:

```
public class MethodsReferenceTeste01 {  
    public static void main(String[] args) {  
        List<Jogos> jogos = new ArrayList<>(List.of(new Jogos("GTA", 1),  
                new Jogos("Red Dead", 3),  
                new Jogos("it take two", 6)));  
        Collections.sort(jogos, JogosComparator::compareByTitle);  
        System.out.println(jogos);  
    }  
}
```

> O código `JogosComparator::compareByTitle` é equivalente a
> `(a1, a2) -> JogosComparator.compareByTitle(a1, a2)`


> [!Example] Saída
> `[Jogos{title='GTA', quatidade=1}, Jogos{title='Red Dead', quatidade=3}, Jogos{title='it take two', quatidade=6}]`
