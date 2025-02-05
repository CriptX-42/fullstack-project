---
Created: 2025-02-05
---

> [!NOTE] Algumas definições
> Ele nos retorna a posição de um objeto numa lista quando buscamos, e também pode retornar **a posição que poderíamos inserir esse objeto caso ele não exista na nossa lista **


Exemplo simples de uso: 
```
public class BinarySearchTest01 {  
    public static void main(String[] args) {  
        List<Integer> numeros = new ArrayList<>();  
        numeros.add(2);  
        numeros.add(0);  
        numeros.add(4);  
        numeros.add(3);  
        Collections.sort(numeros);  
  
        System.out.println("index: " + Collections.binarySearch(numeros, 2)); 
    }  
}
```



> [!Danger] Uso
> - ***Sempre devemos usar o sort antes de usar o binarySearch***
> - O primeiro parametro é nossa lista, o segundo é o valor que queremos buscar


> [!Example] Saída
```
index: 1
```


> [!Warning] Algo a se pensar
> Ele sempre retornar o (- (ponto de inserção) -1)
> Ele só vai retornar o valor positivo **se, e somente se o valor existir**.
> Não pode existir **valor negativo nessa lista**


#### Ordenação customizada
- Para ordenação customizada precisamos passar o *Comparator* como parâmetro de uso: 

```
public static void main(String[] args) {
    JogosByIdComparator jogosByIdComparator = new JogosByIdComparator();  


    List<Jogos> jogos = new ArrayList<>(6);  
    jogos.add(new Jogos(123L, "Resident Evil 3: Nemesys", 3.50));  
    jogos.add(new Jogos(546L, "Medal of Honor", 5.50));  
    jogos.add(new Jogos(897L, "Contra", 5.50));  
    jogos.add(new Jogos(357L, "Metal Slug", 8.50));  
    jogos.add(new Jogos(549L, "Drive I", 6.50));  
    jogos.add(new Jogos(146L, "GTA III", 1.50));  
  
  
  
  
    System.out.println("Com custom sorting 2 ");  
    System.out.println(" ");  
    jogos.sort(jogosByIdComparator);  
  
    Jogos buscando = new Jogos(146L, "GTA III", 1.50);  
  
    for (Jogos jogo:  jogos) {  
        System.out.println(jogo.toString());  
    }  
    System.out.println();  
  
    System.out.println("Index: " +Collections.binarySearch(jogos, buscando, jogosByIdComparator));  
  
}
```


> [!Example] Saída
```
Jogos{id=897, nome='Contra', preco=5.5}
Jogos{id=549, nome='Drive I', preco=6.5}
Jogos{id=146, nome='GTA III', preco=1.5}
Jogos{id=546, nome='Medal of Honor', preco=5.5}
Jogos{id=357, nome='Metal Slug', preco=8.5}
Jogos{id=123, nome='Resident Evil 3: Nemesys', preco=3.5}
==========================================================
Index: 2
```
