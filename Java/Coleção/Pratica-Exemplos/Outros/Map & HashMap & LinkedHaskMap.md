---
Created: 2025-02-08
---

> [!NOTE] Algumas observações
> Map não faz parte da linha de herança da *collection*
> Sempre vai trabalhar com chave (k) e valor (v)

- Exemplo simples de uso

```
public static void main(String[] args) {  
    Map<String, String> map = new HashMap<>();  
    map.put("keyboard","teclado");  
    map.put("mose","mouse");  
  
    System.out.println(map);  
    System.out.println();  
  
    for (String key: map.keySet()) {  
        System.out.println(key + " " + map.get(key));  
    }  
  
    System.out.println();  
  
    for (String values: map.values()) {  
        System.out.println(values);  
  
    }  
  
}
```


> [!Example] Saída
```
{keyboard=teclado, mose=mouse}

keyboard teclado
mose mouse

teclado
mouse
```



> [!Warning] Podemo melhorar
> Podemos trocar o `Map<String, String> map = new HashMap<>();` por `Map<String, String> map = new LinkedHashMap<>();`. Assim vamos ter nosso map baseado na ordem de **inserção**


### Fazendo associações com o MAP

- Imagine que temos a classe *consumidor* e *jogos*, queremos associar a chave consumidor com o valor do jogo (pode ser nome, ou qualquer outro valor). Então teremos:

Classe consumidor:
```
public class Consumidor {  
    private Long id;  
    private String nome;  
  
    public Consumidor( String nome) {  
        this.id = ThreadLocalRandom.current().nextLong(0, 100_000);  
        this.nome = nome;  
    }  
  
    @Override  
    public String toString() {  
        return "Consumidor{" +  
                "id=" + id +  
                ", nome='" + nome + '\'' +  
                '}';  
    }  
  
    @Override  
    public boolean equals(Object o) {  
        if (!(o instanceof Consumidor that)) return false;  
        return Objects.equals(id, that.id) && Objects.equals(nome, that.nome);  
    }  
  
    @Override  
    public int hashCode() {  
        return Objects.hashCode(id);  
    }  
  
    public String getNome() {  
        return nome;  
    }  
  
    public void setNome(String nome) {  
        this.nome = nome;  
    }  
}
```


> [!NOTE] Um adendo no código
> `this.id = ThreadLocalRandom.current().nextLong(0, 100_000);` está gerando números long randomicos

Uso e associação com Jogos:

```
public static void main(String[] args) {  
    Consumidor consumidor1 = new Consumidor("Ricardo");  
    Consumidor consumidor2 = new Consumidor("Redragon");  
  
    Jogos jogos3 = new Jogos(897L, "Contra", 5.50, 2);  
    Jogos jogos4 = new Jogos(146L, "GTA III", 1.50, 2);  
  
    Map<Consumidor, Jogos> consumidorJogosMap = new HashMap<>();  
    consumidorJogosMap.put(consumidor1, jogos4);  
    consumidorJogosMap.put(consumidor2, jogos3);  
  
    for (Map.Entry<Consumidor, Jogos> entry : consumidorJogosMap.entrySet()) {  
        System.out.println(entry.getKey().getNome() + " comprou: " + entry.getValue().getNome());  
    }  
  
}
```


> [!Example] Saída
```
Ricardo comprou: GTA III
Redragon comprou: Contra
```


### Associação 1:*

- Imagine que temos os mesmos objetos acima, tanto *consumidor* quanto *jogos*. Para que possamos associar o consumidor a varios jogos, basta incluirmos os *jogos* numa lista:

```
public static void main(String[] args) {  
    Consumidor consumidor1 = new Consumidor("Ricardo");  
    Consumidor consumidor2 = new Consumidor("Redragon");  
  
    Jogos jogos3 = new Jogos(123L, "Resident Evil 3: Nemesys", 3.50, 1);  
    Jogos jogos4 = new Jogos(546L, "Medal of Honor", 5.50, 2);  
    Jogos jogos5 = new Jogos(897L, "Contra", 5.50, 2);  
    Jogos jogos6 = new Jogos(146L, "GTA III", 1.50, 2);  
  
    List<Jogos> mangaConsumidor1List = List.of(jogos3, jogos5, jogos6);  
    List<Jogos> mangaConsumidor2List = List.of(jogos5, jogos4, jogos5);  
  
    Map<Consumidor, List<Jogos>> consumidorJogosMap = new HashMap<>();  
    consumidorJogosMap.put(consumidor1, mangaConsumidor1List);  
    consumidorJogosMap.put(consumidor2, mangaConsumidor2List);  
  
    for (Map.Entry<Consumidor, List<Jogos>> entry : consumidorJogosMap.entrySet()) {  
        System.out.println(entry.getKey().getNome() + " comprou: ");  
  
        for (Jogos jogos : entry.getValue()) {  
            System.out.println(jogos);  
        }  
  
    }  
  
}
```


> [!Example] Saída
```
Redragon comprou: 
Jogos{id=897, nome='Contra', preco=5.5, quantidade=2}
Jogos{id=546, nome='Medal of Honor', preco=5.5, quantidade=2}
Jogos{id=897, nome='Contra', preco=5.5, quantidade=2}

Ricardo comprou: 
Jogos{id=123, nome='Resident Evil 3: Nemesys', preco=3.5, quantidade=1}
Jogos{id=897, nome='Contra', preco=5.5, quantidade=2}
Jogos{id=146, nome='GTA III', preco=1.5, quantidade=2}
```
