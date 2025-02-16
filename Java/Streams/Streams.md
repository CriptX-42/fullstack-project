---
Created: 2025-02-16
tags:
  - Dicionário
---

> [!NOTE] Uma breve descrição
> Streams são uma forma de processamento de dados que ajuda a fazer as funcionalidades numa coleção de uma forma funcional e encadeada
> 
> Um stream tem 2 operações. Intermediarias ou finais:
> 1. Uma ação intermediaria retorna o proprio stream


> [!Tip] Sumário
> 1. [[FlatMap]]


### O problema (Introdução)
	Imagine que temos uma classe de jogos, e queremos fazer uma lista com preços e titulos
	Queremos ordenar por nome, e depois retornar os 3 primeiros jogos com preço menor que 4

### Modo sem Stream

- Classe de domínio

```
public class Jogos {  
    private String nome;  
    private double Price;  
  
    public Jogos(String nome, double price) {  
        this.nome = nome;  
        Price = price;  
    }  
  
    @Override  
    public String toString() {  
        return "Jogos{" +  
                "nome='" + nome + '\'' +  
                ", Price=" + Price +  
                '}';  
    }  
  
    public String getNome() {  
        return nome;  
    }  
  
    public double getPrice() {  
        return Price;  
    }  
}
```

- Classe de uso
```
public class Teste01 {  
    private static List<Jogos> listaJogos = new ArrayList<>(List.of(new Jogos("GTA", 12.3),  
            new Jogos("Gran turismo", 3.55),  
            new Jogos("007 Golden Eye", 2.95),  
            new Jogos("Contra", 6.66),  
            new Jogos("DOOM", 7.11),  
            new Jogos("Medal of Honor", 1.99),  
            new Jogos("Zelda: Ocarine of the time", 1)));  
  
    public static void main(String[] args) {  
        listaJogos.sort(Comparator.comparing(Jogos::getNome));  
        List<String> jogosBaratos = new ArrayList<>();  
        for (Jogos listaJogo : listaJogos) {  
            if(listaJogo.getPrice() <= 4) {  
                jogosBaratos.add(listaJogo.getNome());  
            }  
            if(jogosBaratos.size() >= 3) {  
                break;  
            }  
  
        }  
  
        System.out.println(listaJogos);  
        System.out.println(jogosBaratos);  
  
    }  
}
```


> [!Example] Saída
```
[Jogos{nome='007 Golden Eye', Price=2.95}, Jogos{nome='Contra', Price=6.66}, Jogos{nome='DOOM', Price=7.11}, Jogos{nome='GTA', Price=12.3}, Jogos{nome='Gran turismo', Price=3.55}, Jogos{nome='Medal of Honor', Price=1.99}, Jogos{nome='Zelda: Ocarine of the time', Price=1.0}]

[007 Golden Eye, Gran turismo, Medal of Honor]
```


### Resolvendo com Streams

```
public class Teste02 {  
    private static List<Jogos> listaJogos = new ArrayList<>(List.of(new Jogos("GTA", 12.3),  
            new Jogos("Gran turismo", 3.55),  
            new Jogos("007 Golden Eye", 2.95),  
            new Jogos("Contra", 6.66),  
            new Jogos("DOOM", 7.11),  
            new Jogos("Medal of Honor", 1.99),  
            new Jogos("Zelda: Ocarine of the time", 1)));  
  
    public static void main(String[] args) {  
        listaJogos.sort(Comparator.comparing(Jogos::getNome));  
        List<String> list = listaJogos.stream()  
                .sorted(Comparator.comparing(Jogos::getNome))  
                .filter(lista -> lista.getPrice() <= 4)  
                .limit(3)  
                .map(Jogos::getNome)  
                .toList();  
  
        System.out.println(listaJogos);  
        System.out.println(list);  
  
    }  
}
```


> [!Example] Saída
```
[Jogos{nome='007 Golden Eye', Price=2.95}, Jogos{nome='Contra', Price=6.66}, Jogos{nome='DOOM', Price=7.11}, Jogos{nome='GTA', Price=12.3}, Jogos{nome='Gran turismo', Price=3.55}, Jogos{nome='Medal of Honor', Price=1.99}, Jogos{nome='Zelda: Ocarine of the time', Price=1.0}]

[007 Golden Eye, Gran turismo, Medal of Honor]
```

> [!Example] Explicação
> **Streams**: vai permitir processar os elementos de forma funcional e encadeada
> **.filter**: vai filtrar os jgoos com o preço menor que 4
> **limit**: pega apenas os 3 primeiros jogos após a filtragem
> **Map:** vai extrair apenas nome do jogo
> **toList()**: converte o fluxo final para uma List<String>, que pode ser usada normalmente

Se eu tiver que chamar 2 streams de uma unica fonte, terei que instanciar a lista novamente e chamar o stream, EX:
listaJogos.stream()... (chamando a segunda vez)
