---
Created: 2025-02-07
---

> [!Danger] O que não fazer
> Não é uma boa ideia remover um item da lista usando o **foreach**

#### Solução

> [!Tip] Uma boa classe
> **Iterator** ele verifica uma fila antes de fazer uma ação na sua lista


#### Exemplo: 

- Imagine a seguinte classe:

```
public class Jogos implements Comparable<Jogos> {  
  
    private Long id;  
    private String nome;  
    private double preco;  
    private int quantidade;  
  
    public Jogos(Long id, String nome, double preco) {  
        Objects.requireNonNull(id, "Não pode ser nulo");  
        this.id = id;  
        this.nome = nome;  
        this.preco = preco;  
    }  
  
    public Jogos(Long id, String nome, double preco, int quantidade) {  
        this(id, nome, preco);  
        this.quantidade = quantidade;  
    }  

....
  
    @Override  
    public String toString() {  
        return "Jogos{" +  
                "id=" + id +  
                ", nome='" + nome + '\'' +  
                ", preco=" + preco +  
                ", quantidade=" + quantidade +  
                '}';  
    }  
  
   ...
}
```

- E o seguinte uso: 

```
public static void main(String[] args) {  
    List<Jogos> jogos = new ArrayList<>(6);  
    JogosByIdComparator jogosByIdComparator = new JogosByIdComparator();  
    jogos.add(new Jogos(123L, "Resident Evil 3: Nemesys", 3.50, 1));  
    jogos.add(new Jogos(546L, "Medal of Honor", 5.50, 2));  
    jogos.add(new Jogos(897L, "Contra", 5.50, 2));  
    jogos.add(new Jogos(357L, "Metal Slug", 8.50, 2));  
    jogos.add(new Jogos(549L, "Drive I", 6.50, 2));  
    jogos.add(new Jogos(146L, "GTA III", 1.50, 2));  
  
    Iterator<Jogos> jogosIterator = jogos.iterator();  
  
    while (jogosIterator.hasNext()) {  
        Jogos jogo = jogosIterator.next();  
        if(jogo.getQuantidade() == 2) {  
            jogosIterator.remove();  
        }  
    }  
  
    System.out.println(jogos);  
}
```


> [!Example] Saida
> `[Jogos{id=123, nome='Resident Evil 3: Nemesys', preco=3.5, quantidade=1}]`


> [!Warning] Alguns adendos
> `hasNext()` vai retornar boolean, true enquanto a fila existir
> 

