---
Created: 2025-02-15
---


# O problema
- Imagine que temos um cadastro de jogos
	Se acharmos um jogo por Titulo, alteramos o titulo
	Se não acharmos por ID, voltamos um erro
	Se não acharmos por Titulo, incluímos um novo jogo


- Temos essa classe de dominio
```
public class Jogos {  
    private Integer id;  
    private String title;  
    private int qtdade;  
  
    public Jogos(Integer id, String title, int qtdade) {  
        this.id = id;  
        this.title = title;  
        this.qtdade = qtdade;  
    }  
  
    @Override  
    public String toString() {  
        return "Jogos{" +  
                "id=" + id +  
                ", title='" + title + '\'' +  
                ", qtdade=" + qtdade +  
                '}';  
    }  
  
    public void setTitle(String title) {  
        this.title = title;  
    }  
  
    public void setQtdade(int qtdade) {  
        this.qtdade = qtdade;  
    }  
  
    public Integer getId() {  
        return id;  
    }  
  
    public String getTitle() {  
        return title;  
    }  
  
    public int getQtdade() {  
        return qtdade;  
    }  
}
```

- Repositori

```
public class JogosRepository {  
    private static List<Jogos> jogos = List.of(new Jogos(1, "GTA II", 3), new Jogos(2, "The sims", 1), new Jogos(1, "Contra", 10));  
  
    public static Optional<Jogos>  findByTitle(String title) {  
        return findBy(j -> j.getTitle().equals(title));  
    }  
  
    public static Optional<Jogos>  findById(Integer id) {  
        return findBy(j -> j.getId().equals(id));  
    }  
  
    public static Optional<Jogos>  findBy(Predicate<Jogos> predicate) {  
        Jogos found = null;  
        for(Jogos jogo: jogos) {  
            if(predicate.test(jogo)) {  
                found = jogo;  
            }  
        }  
        return Optional.ofNullable(found);  
    }  
}
```

- Classe de teste

```
public static void main(String[] args) {  
    Optional<Jogos> jogoPorTitulo = JogosRepository.findByTitle("GTA II");  
    jogoPorTitulo.ifPresent(j -> j.setTitle("GTA III"));  
    System.out.println(jogoPorTitulo);  
  
    Jogos jogoPorId = JogosRepository.findById(1).orElseThrow(IllegalArgumentException::new);  
    System.out.println(jogoPorId);  
  
    Jogos findByTitle = JogosRepository.findByTitle("DayZ")  
            .orElseGet(() -> new Jogos(3, "DayZ", 20));  
  
    System.out.println(jogoPorId);  
  
}
```


> [!Example] Saída
```
Optional[Jogos{id=1, title='GTA III', qtdade=3}]
Jogos{id=1, title='Contra', qtdade=10}
Jogos{id=1, title='Contra', qtdade=10}
```
