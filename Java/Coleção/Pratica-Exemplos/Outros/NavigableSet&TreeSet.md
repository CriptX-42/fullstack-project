---
Created: 2025-02-08
tags:
  - Duvidas
---
#### NavigableSet


> [!NOTE] Definição
> Adiciona alguns métodos que podemos trabalhar para pegar elementos existentes 
> Quando vemos a palavra `Tree` significa que é uma classe que vai trabalhar com partes de Sort
> O que precisamos saber é que o `TreeSet` vai fazer a comparação baseada no **compareTo** da nossa classe objeto
> Só usamos isso quando usarmos juntos o **comparator** ou **comparable**


> [!Warning] Alguns cuidados
> Ele falha no contrato do set, ou seja, não usa o **equals** para verificar se os elementos são iguais

### Um exemplo errado

- Imagine que temos esse código usando o `NavegableSet` e `TreeSet`

```
public static void main(String[] args) {  
    NavigableSet<Smartphone> set = new TreeSet<>();  
    Smartphone smartphone = new Smartphone("123", "Nokia");  
      
}
```

Caso tentarmos colocar isso dentro um set `set.add(smartphone);` ou seja, adicionar o smartphone dentro do nosso ***set***. Teríamos o seguinte erro:

> [!Danger] saída
```
Exception in thread "main" java.lang.ClassCastException: class YColecoes.Domain.Smartphone cannot be cast to class java.lang.Comparable (YColecoes.Domain.Smartphone is in unnamed module of loader 'app'; java.lang.Comparable is in module java.base of loader 'bootstrap')
	at java.base/java.util.TreeMap.compare(TreeMap.java:1606)
	at java.base/java.util.TreeMap.addEntryToEmptyMap(TreeMap.java:811)
	at java.base/java.util.TreeMap.put(TreeMap.java:820)
	at java.base/java.util.TreeMap.put(TreeMap.java:569)
	at java.base/java.util.TreeSet.add(TreeSet.java:259)
	at YColecoes.test.NavigableSetTest01.main(NavigableSetTest01.java:12)
```

- Ele esta tentando ver se Smartphone é um `comparable` por isso lança essa exceção


## Modo certo de adicionarmos a lista dentro do **set**

- Vamos colocar um `Comparator()` na criação do nosso TreeSet

	Exemplo de comparator com a marca do smartphone

```
class SmartphoneMarcaComparator implements Comparator <Smartphone> {  
    @Override  
    public int compare(Smartphone o1, Smartphone o2) {  
        return o1.getMarca().compareTo(o2.getMarca());  
    }  
}  

public class NavigableSetTest01 {  
    public static void main(String[] args) {  
        NavigableSet<Smartphone> set = new TreeSet<>(new SmartphoneMarcaComparator());  
        Smartphone smartphone = new Smartphone("123", "Nokia");  
        set.add(smartphone);  
  
        System.out.println(set);  
    }  
}
```


> [!Example] Saída
```
[Smartphone{serialNumber='123', marca='Nokia'}]
```


### Outro exemplo com a classe *jogos*

 - Temos o **comparteTo** comparando com o nome do jogo:

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
  
   ...
  
    @Override  
    public int compareTo(Jogos outroJogo) {  
       return this.nome.compareTo(outroJogo.getNome());  
    }  
}
```

- O seguinte uso:

```
public static void main(String[] args) {  
  
    NavigableSet<Jogos> jogos = new TreeSet<>();  
    jogos.add(new Jogos(123L, "Resident Evil 3: Nemesys", 3.50, 1));  
    jogos.add(new Jogos(546L, "Medal of Honor", 5.50, 2));  
    jogos.add(new Jogos(897L, "Contra", 5.50, 2));  
    jogos.add(new Jogos(357L, "Metal Slug", 8.50, 2));  
    jogos.add(new Jogos(357L, "Metal Slug", 8.50, 2));  
    jogos.add(new Jogos(549L, "Drive I", 6.50, 2));  
    jogos.add(new Jogos(146L, "GTA III", 1.50, 2));  
  
    for (Jogos jogo: jogos) {  
        System.out.println(jogo);  
    }  
}
```

- A saída vai ser ordenada pelo **nome do jogo**:

> [!Example] Saída
```
Jogos{id=897, nome='Contra', preco=5.5, quantidade=2}
Jogos{id=549, nome='Drive I', preco=6.5, quantidade=2}
Jogos{id=146, nome='GTA III', preco=1.5, quantidade=2}
Jogos{id=546, nome='Medal of Honor', preco=5.5, quantidade=2}
Jogos{id=357, nome='Metal Slug', preco=8.5, quantidade=2}
Jogos{id=123, nome='Resident Evil 3: Nemesys', preco=3.5, quantidade=1}
```


#### Os métodos que nos ajudam 
 - Agora que estamos usando o Navegable e o TreeSet, podemos usar alguns métodos muito bons na nossa lista:

```
for (Jogos jogo: jogos.descendingSet()) {  
    System.out.println(jogo);  
}
```

> Carrega a mesma lista mas com ordem dessedente


#### lower
 - Vai trazer o que é menor
```
NavigableSet<Jogos> jogos = new TreeSet<>(new JogosPrecoComparator());  
jogos.add(new Jogos(123L, "Resident Evil 3: Nemesys", 3.50, 1));  
jogos.add(new Jogos(546L, "Medal of Honor", 5.50, 2));  
jogos.add(new Jogos(897L, "Contra", 5.50, 2));  
jogos.add(new Jogos(357L, "Metal Slug", 8.50, 2));  
jogos.add(new Jogos(357L, "Metal Slug", 8.50, 2));  
jogos.add(new Jogos(549L, "Drive I", 6.50, 2));  
jogos.add(new Jogos(146L, "GTA III", 1.50, 2));  
  
Jogos mario = new Jogos(5L, "Mario", 5.50, 2);  
System.out.println(jogos.lower(mario));
```


> [!Example] Saída
```
Jogos{id=123, nome='Resident Evil 3: Nemesys', preco=3.5, quantidade=1}
```


#### floor
- O mesmo valor ou o imediato logo embaixo dele
```
NavigableSet<Jogos> jogos = new TreeSet<>(new JogosPrecoComparator());  
jogos.add(new Jogos(123L, "Resident Evil 3: Nemesys", 3.50, 1));  
jogos.add(new Jogos(546L, "Medal of Honor", 5.50, 2));  
jogos.add(new Jogos(897L, "Contra", 5.50, 2));  
jogos.add(new Jogos(357L, "Metal Slug", 8.50, 2));  
jogos.add(new Jogos(357L, "Metal Slug", 8.50, 2));  
jogos.add(new Jogos(549L, "Drive I", 6.50, 2));  
jogos.add(new Jogos(146L, "GTA III", 1.50, 2));  
  
Jogos mario = new Jogos(5L, "Mario", 5.50, 2);  
System.out.println(jogos.lower(mario));
```

> [!Example] Saída
```
Jogos{id=546, nome='Medal of Honor', preco=5.5, quantidade=2}
```


#### higher
- O primeiro maior
```
NavigableSet<Jogos> jogos = new TreeSet<>(new JogosPrecoComparator());  
jogos.add(new Jogos(123L, "Resident Evil 3: Nemesys", 3.50, 1));  
jogos.add(new Jogos(546L, "Medal of Honor", 5.50, 2));  
jogos.add(new Jogos(897L, "Contra", 5.50, 2));  
jogos.add(new Jogos(357L, "Metal Slug", 8.50, 2));  
jogos.add(new Jogos(357L, "Metal Slug", 8.50, 2));  
jogos.add(new Jogos(549L, "Drive I", 6.50, 2));  
jogos.add(new Jogos(146L, "GTA III", 1.50, 2));  
  
Jogos mario = new Jogos(5L, "Mario", 5.50, 2);  
System.out.println(jogos.lower(mario));
```

> [!Example] Saída
`Jogos{id=549, nome='Drive I', preco=6.5, quantidade=2}`
#### ceiling
 - Igual ou maior, levando em consideração o valor que nós passarmos
```
NavigableSet<Jogos> jogos = new TreeSet<>(new JogosPrecoComparator());  
jogos.add(new Jogos(123L, "Resident Evil 3: Nemesys", 3.50, 1));  
jogos.add(new Jogos(546L, "Medal of Honor", 5.50, 2));  
jogos.add(new Jogos(897L, "Contra", 5.50, 2));  
jogos.add(new Jogos(357L, "Metal Slug", 8.50, 2));  
jogos.add(new Jogos(357L, "Metal Slug", 8.50, 2));  
jogos.add(new Jogos(549L, "Drive I", 6.50, 2));  
jogos.add(new Jogos(146L, "GTA III", 1.50, 2));  
  
Jogos mario = new Jogos(5L, "Mario", 5.50, 2);  
System.out.println(jogos.lower(mario));
```


> [!Example] Saída
`Jogos{id=546, nome='Medal of Honor', preco=5.5, quantidade=2}`


#### Excluindo elementos da lista (o primeiro e o ultimo)
``
`jogos.pollFirst()`
`jogos.pollLast()`