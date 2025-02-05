---
Created: 2025-02-05
---
#### Comparação customizada sem wrapper


> [!Warning] Regras
> 1. Negativo se o this < 'outroJogo'
> 2. Se o this == 'outroJogo' return 0
> 3. Se o this > 'outroJogo' return positivo


```
public class Jogos implements Comparable<Jogos> {  
  
    private Long id;  
    private String nome;  
    private double preco;  
  
    public Jogos(Long id, String nome, double preco) {  
        Objects.requireNonNull(id, "Não pode ser nulo");  
        this.id = id;  
        this.nome = nome;  
        this.preco = preco;  
    }  
  
  
    ...
  
    @Override  
    public int compareTo(Jogos outroJogo) {  
	    if(this.id < outroJogo.getId()) return -1;  
		if(this.id.equals(outroJogo.getId())) return 0;  
		return 1;  
    }  
}
```

#### Implementação com wrapper (mais simples)

```
public class Jogos implements Comparable<Jogos> {  
  
    private Long id;  
    private String nome;  
    private double preco;  
  
    public Jogos(Long id, String nome, double preco) {  
        Objects.requireNonNull(id, "Não pode ser nulo");  
        this.id = id;  
        this.nome = nome;  
        this.preco = preco;  
    }  
  ...
  
    @Override  
    public int compareTo(Jogos outroJogo) {  
       return this.id.compareTo(outroJogo.getId());  
    }  
}
```


- Uso:

```
public static void main(String[] args) {  
    List<Jogos> jogos = new ArrayList<>(6);  
  
    jogos.add(new Jogos(123L, "Resident Evil 3: Nemesys", 3.50));  
    jogos.add(new Jogos(546L, "Medal of Honor", 5.50));  
    jogos.add(new Jogos(897L, "Contra", 5.50));  
    jogos.add(new Jogos(357L, "Metal Slug", 8.50));  
    jogos.add(new Jogos(549L, "Drive I", 6.50));  
    jogos.add(new Jogos(146L, "GTA III", 1.50));  
  
    Collections.sort(jogos);  
    System.out.println("Com custom sorting");  
    for (Jogos jogo:  jogos) {  
        System.out.println(jogo);  
    }  
}
```

> [!Example] Saída para os dois códigos
```
Com custom sorting

Jogos{id=123, nome='Resident Evil 3: Nemesys', preco=3.5}
Jogos{id=146, nome='GTA III', preco=1.5}
Jogos{id=357, nome='Metal Slug', preco=8.5}
Jogos{id=546, nome='Medal of Honor', preco=5.5}
Jogos{id=549, nome='Drive I', preco=6.5}
Jogos{id=897, nome='Contra', preco=5.5}
```
