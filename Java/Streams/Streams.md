---
Created: 2025-02-16
---

> [!NOTE] Uma breve descrição
> Streams são uma forma de processamento de dados que ajuda a fazer as funcionalidades numa coleção de uma forma funcional


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
