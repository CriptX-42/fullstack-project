---
Created: 2025-02-17
---
#### Agrupando jogos por categoria

- Imagine que queremos agrupar jogos por categoria usando o Stream

- Nosso enum
```
public enum Category {  
    ACAO, AVENTURA, TIRO_PRIMEIRA_PESSOA  
}
```

- Nossa classe de dominio:

```
public class Jogos {  
    private String nome;  
    private double Price;  
    private Category category;  
  
    public Jogos(String nome, double price) {  
        this.nome = nome;  
        Price = price;  
    }  
  
    public Jogos(String nome, double price, Category category) {  
        this.nome = nome;  
        Price = price;  
        this.category = category;  
    }  
  
    @Override  
    public boolean equals(Object o) {  
        if (!(o instanceof Jogos jogos)) return false;  
        return Objects.equals(nome, jogos.nome);  
    }  
  
    @Override  
    public int hashCode() {  
        return Objects.hashCode(nome);  
    }  
  
    @Override  
    public String toString() {  
        return "Jogos{" +  
                "nome='" + nome + '\'' +  
                ", Price=" + Price +  
                ", category=" + category +  
                '}';  
    }  
  
    public Category getCategory() {  
        return category;  
    }  
  
    public String getNome() {  
        return nome;  
    }  
  
    public double getPrice() {  
        return Price;  
    }  
	}
```

- Nosso Stream com o groupBy

```
public class Teste12 {  
    private static List<Jogos> listaJogos = new ArrayList<>(List.of(new Jogos("GTA", 12.3, Category.ACAO),  
            new Jogos("Gran turismo", 3.55, Category.ACAO),  
            new Jogos("007 Golden Eye", 2.95, Category.TIRO_PRIMEIRA_PESSOA),  
            new Jogos("Contra", 6.66, Category.ACAO),  
            new Jogos("DOOM", 7.11, Category.TIRO_PRIMEIRA_PESSOA),  
            new Jogos("Medal of Honor", 1.99, Category.TIRO_PRIMEIRA_PESSOA),  
            new Jogos("Zelda: Ocarine of the time", 1, Category.AVENTURA)));  
  
    public static void main(String[] args) {  
  
        Map<Category, List<Jogos>> collect = listaJogos.stream().collect(Collectors.groupingBy(Jogos::getCategory));  
        System.out.println(collect);  
    }  
}
```


> [!Example] Saída
```
{
   "ACAO="[
      "Jogos"{
         "nome=""GTA",
         Price=12.3,
         "category=ACAO"
      },
      "Jogos"{
         "nome=""Gran turismo",
         Price=3.55,
         "category=ACAO"
      },
      "Jogos"{
         "nome=""Contra",
         Price=6.66,
         "category=ACAO"
      }
   ],
   "AVENTURA="[
      "Jogos"{
         "nome=""Zelda: Ocarine of the time",
         Price=1.0,
         "category=AVENTURA"
      }
   ],
   "TIRO_PRIMEIRA_PESSOA="[
      "Jogos"{
         "nome=""007 Golden Eye",
         Price=2.95,
         "category=TIRO_PRIMEIRA_PESSOA"
      },
      "Jogos"{
         "nome=""DOOM",
         Price=7.11,
         "category=TIRO_PRIMEIRA_PESSOA"
      },
      "Jogos"{
         "nome=""Medal of Honor",
         Price=1.99,
         "category=TIRO_PRIMEIRA_PESSOA"
      }
   ]
}
```


### Mais uma aplicação em *jogos*

Imagine que temos esse enum:

```
public enum Promotion {  
    UNDER_PROMOTION, NORMAL_PRACE  
}
```

Queremos agrupar os jogos menores que 6 reais como **com promoção** e os jogos maiores que isso como **sem promoção** mas tudo isso sem interferir no objeto *jogos*. Fariamos dessa maneira:

```
public class Teste13 {  
    private static List<Jogos> listaJogos = new ArrayList<>(List.of(new Jogos("GTA", 12.3, Category.ACAO),  
            new Jogos("Gran turismo", 3.55, Category.ACAO),  
            new Jogos("007 Golden Eye", 2.95, Category.TIRO_PRIMEIRA_PESSOA),  
            new Jogos("Contra", 6.66, Category.ACAO),  
            new Jogos("DOOM", 7.11, Category.TIRO_PRIMEIRA_PESSOA),  
            new Jogos("Medal of Honor", 1.99, Category.TIRO_PRIMEIRA_PESSOA),  
            new Jogos("Zelda: Ocarine of the time", 1, Category.AVENTURA)));  
  
    public static void main(String[] args) {  
  
        Map<Promotion, List<Jogos>> collect = listaJogos.stream()  
                .collect(  
                        Collectors.groupingBy(listaJogo -> listaJogo.getPrice() < 6 ? Promotion.UNDER_PROMOTION : Promotion.NORMAL_PRACE));  
  
        System.out.println(collect);  
    }  
}
```


> [!Example] Saída
```
{UNDER_PROMOTION=[Jogos{nome='Gran turismo', Price=3.55, category=ACAO}, Jogos{nome='007 Golden Eye', Price=2.95, category=TIRO_PRIMEIRA_PESSOA}, Jogos{nome='Medal of Honor', Price=1.99, category=TIRO_PRIMEIRA_PESSOA}, Jogos{nome='Zelda: Ocarine of the time', Price=1.0, category=AVENTURA}], NORMAL_PRACE=[Jogos{nome='GTA', Price=12.3, category=ACAO}, Jogos{nome='Contra', Price=6.66, category=ACAO}, Jogos{nome='DOOM', Price=7.11, category=TIRO_PRIMEIRA_PESSOA}]}
```


### Uma curiosidade

Podemos agrupar GroupingBy:

```
public static void main(String[] args) {  
  
    Map<Promotion, Map<Category, List<Jogos>>> collect = listaJogos.stream()  
            .collect(  
                    Collectors.groupingBy(listaJogo -> listaJogo.getPrice() < 6 ? Promotion.UNDER_PROMOTION : Promotion.NORMAL_PRACE, Collectors.groupingBy(Jogos::getCategory)));  
  
  
    System.out.println(collect);  
}
```


> [!Example] Saída
```
{NORMAL_PRACE={TIRO_PRIMEIRA_PESSOA=[Jogos{nome='DOOM', Price=7.11, category=TIRO_PRIMEIRA_PESSOA}], ACAO=[Jogos{nome='GTA', Price=12.3, category=ACAO}, Jogos{nome='Contra', Price=6.66, category=ACAO}]}, UNDER_PROMOTION={TIRO_PRIMEIRA_PESSOA=[Jogos{nome='007 Golden Eye', Price=2.95, category=TIRO_PRIMEIRA_PESSOA}, Jogos{nome='Medal of Honor', Price=1.99, category=TIRO_PRIMEIRA_PESSOA}], ACAO=[Jogos{nome='Gran turismo', Price=3.55, category=ACAO}], AVENTURA=[Jogos{nome='Zelda: Ocarine of the time', Price=1.0, category=AVENTURA}]}}
```


### Brincando com groupingBy

```
public static void main(String[] args) {  
  
    Map<Category, Long> collect = listaJogos.stream().collect(Collectors.groupingBy(Jogos::getCategory, Collectors.counting()));  
  
    System.out.println(collect);  
    Map<Category, Optional<Jogos>> collect1 = listaJogos.stream().collect(Collectors.groupingBy(Jogos::getCategory, Collectors.maxBy(Comparator.comparing(Jogos::getPrice))));  
    System.out.println(collect1);  
  
    Map<Category, Jogos> collect2 = listaJogos.stream().collect(Collectors.groupingBy(Jogos::getCategory, Collectors.collectingAndThen(Collectors.maxBy(Comparator.comparing(Jogos::getPrice)), Optional::get)));  
  
    System.out.println(collect2);  
}
```



> [!Example] Saída
```
{AVENTURA=1, TIRO_PRIMEIRA_PESSOA=3, ACAO=3}

{AVENTURA=Optional[Jogos{nome='Zelda: Ocarine of the time', Price=1.0, category=AVENTURA}], TIRO_PRIMEIRA_PESSOA=Optional[Jogos{nome='DOOM', Price=7.11, category=TIRO_PRIMEIRA_PESSOA}], ACAO=Optional[Jogos{nome='GTA', Price=12.3, category=ACAO}]}

{AVENTURA=Jogos{nome='Zelda: Ocarine of the time', Price=1.0, category=AVENTURA}, TIRO_PRIMEIRA_PESSOA=Jogos{nome='DOOM', Price=7.11, category=TIRO_PRIMEIRA_PESSOA}, ACAO=Jogos{nome='GTA', Price=12.3, category=ACAO}}
```


```
public static void main(String[] args) {  
  
    //Gostariamos de agrupoar por categoria e tirar estatistica disso  
  
    Map<Category, DoubleSummaryStatistics> collect = listaJogos.stream().collect(Collectors.groupingBy(Jogos::getCategory, Collectors.summarizingDouble(Jogos::getPrice)));  
  
    System.out.println(collect);  
  
    //Não se repete  
    Map<Category, Set<Promotion>> collect1 = listaJogos.stream().collect(Collectors.groupingBy(Jogos::getCategory, Collectors.mapping(Teste15::getPromotion, Collectors.toSet())));  
  
    System.out.println(collect1);  
  
    // Mantem a ordem de inserção  
    Map<Category, LinkedHashSet<Promotion>> collect2 = listaJogos.stream().collect(Collectors.groupingBy(Jogos::getCategory, Collectors.mapping(Teste15::getPromotion, Collectors.toCollection(LinkedHashSet::new))));  
  
    System.out.println(collect2);  
  
}
```



> [!Example] Saída
```
{AVENTURA=DoubleSummaryStatistics{count=1, sum=1,000000, min=1,000000, average=1,000000, max=1,000000}, ACAO=DoubleSummaryStatistics{count=3, sum=22,510000, min=3,550000, average=7,503333, max=12,300000}, TIRO_PRIMEIRA_PESSOA=DoubleSummaryStatistics{count=3, sum=12,050000, min=1,990000, average=4,016667, max=7,110000}}

{AVENTURA=[UNDER_PROMOTION], ACAO=[NORMAL_PRACE, UNDER_PROMOTION], TIRO_PRIMEIRA_PESSOA=[NORMAL_PRACE, UNDER_PROMOTION]}

{AVENTURA=[UNDER_PROMOTION], ACAO=[NORMAL_PRACE, UNDER_PROMOTION], TIRO_PRIMEIRA_PESSOA=[UNDER_PROMOTION, NORMAL_PRACE]}
```
