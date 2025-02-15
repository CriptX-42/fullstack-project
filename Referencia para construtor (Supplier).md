---
Created: 2025-02-13
---

> [!NOTE] Definição
> É a referencia para um construtor, nós podemos utilizar lambda para criar um objeto
> O Suppler só faz pegar um **result** e retornar um **result**

### Uso

```
public class MethodsReference04 {  
    public static void main(String[] args) {  
        Supplier<JogosComparator> newJogosComparator = JogosComparator::new;  
        JogosComparator jogosComparator = newJogosComparator.get(); // aqui é a instancia  
        List<Jogos> jogos = new ArrayList<>(List.of(new Jogos("GTA", 1),  
                new Jogos("Red Dead", 3),  
                new Jogos("it take two", 6)));  
  
        jogos.sort(jogosComparator::compareByTitleNonStatic);  
  
        System.out.println(jogos);  
  
    }  
}
```

> newJogosComparator.get(); é a instancia do meu objeto
