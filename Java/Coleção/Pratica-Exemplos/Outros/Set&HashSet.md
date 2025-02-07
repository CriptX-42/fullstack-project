---
Created: 2025-02-07
---

> [!NOTE] Vantagens
> o *Set* não permite itens duplicados na coleção
> Se usarmos o `HashSet` ele além de permitir elementos únicos, vai organizar nossa estrutura. Com base no nosso Equals e hashCode
> Não é indexado, não temos como pegar a posição, apenas navegar sobre a coleção

Exemplo:

```
public class SetTest01 {  
  
    public static void main(String[] args) {  
        Set<Jogos> jogos = new HashSet<>();  
        JogosByIdComparator jogosByIdComparator = new JogosByIdComparator();  
        jogos.add(new Jogos(123L, "Resident Evil 3: Nemesys", 3.50, 1));  
        jogos.add(new Jogos(546L, "Medal of Honor", 5.50, 2));  
        jogos.add(new Jogos(897L, "Contra", 5.50, 2));  
        jogos.add(new Jogos(357L, "Metal Slug", 8.50, 2));  
        jogos.add(new Jogos(357L, "Metal Slug", 8.50, 2));  
        jogos.add(new Jogos(549L, "Drive I", 6.50, 2));  
        jogos.add(new Jogos(146L, "GTA III", 1.50, 2));  
  
  
        for (Jogos jogo:  jogos) {  
            System.out.println(jogo);  
        }  
    }  
}
```


> [!Example] Saída
```
Jogos{id=123, nome='Resident Evil 3: Nemesys', preco=3.5, quantidade=1}
Jogos{id=549, nome='Drive I', preco=6.5, quantidade=2}
Jogos{id=546, nome='Medal of Honor', preco=5.5, quantidade=2}
Jogos{id=897, nome='Contra', preco=5.5, quantidade=2}
Jogos{id=146, nome='GTA III', preco=1.5, quantidade=2}
Jogos{id=357, nome='Metal Slug', preco=8.5, quantidade=2} 
```
