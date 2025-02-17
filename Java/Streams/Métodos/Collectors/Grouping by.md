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
