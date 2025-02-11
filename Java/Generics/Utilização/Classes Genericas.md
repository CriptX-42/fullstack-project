---
Created: 2025-02-10
---

> [!Example] O problema
> Temos dois objetos *carro* e *barco*. Temos que criar 1 serviço para gerenciar a locação desses dois objetos de forma generica

### Modo menos pratico

- Objetos *carro* e *barco*

```
public class Barco {  
    private String nome;  
  ...
}
```

```
public class Carro {  
    private String nome;  
 ...
}
```

Serviço **Barco** (nota que teríamos de desenvolver um serviço para carro também, o que seria custoso)

```
public class BarcoRentavelService {  
    private List<Barco> barcosDisponiveis = new ArrayList<>(  
            List.of(new Barco("Lancha"), new Barco("Iate")));  
  
    public Barco buscarCarroDisponivel() {  
        System.out.println("Buscando Barco Disponivel...");  
        Barco barco = barcosDisponiveis.remove(0);  
        System.out.println("Alugando barco: " + barco);  
  
        System.out.println("Barco disponiveis para alugar: " + barco);  
  
        System.out.println(barcosDisponiveis);  
        return barco;  
    }  
  
    public void retornarCarroAlugado(Barco barco) {  
        System.out.println("Devolvendo barco " + barco);  
        barcosDisponiveis.add(barco);  
        System.out.println("Carros para alugar " );  
        System.out.println(barcosDisponiveis);  
  
  
    }  
}
```

- Uso da classe de serviço

```
public class ClasseGenericaTeste01 {  
    public static void main(String[] args) {  
        RentavelService carroRentavelService = new RentavelService();  
        Carro carro = carroRentavelService.buscarCarroDisponivel();  
        System.out.println("Usando carro por 1 mês...");  
        carroRentavelService.retornarCarroAlugado(carro);  
    }  
}
```

### Deixando o serviço generico

- Criando um serviço genérico para locação de carro 

```
public class RentavelService<T> {  
    private List<T> veiculosDisponiveis;  
  
    public RentavelService(List<T> objetoDisponiveis) {  
        this.veiculosDisponiveis = objetoDisponiveis;  
    }  
  
    public T buscarVeiculosDisponiveis() {  
        System.out.println("Buscando veiculo Disponivel...");  
        T t = veiculosDisponiveis.remove(0);  
        System.out.println("Alugando veiculo: " + t);  
  
        System.out.println("Veiculo disponiveis para alugar: " + t);  
  
        System.out.println(t);  
        return t;  
    }  
  
    public void retornarVeiculoAlugado(T veiculo) {  
        System.out.println("Devolvendo veiculo " + veiculo);  
        veiculosDisponiveis.add(veiculo);  
        System.out.println("Carros para alugar " );  
        System.out.println(veiculosDisponiveis);  
    }  
}
```

- O Uso do generico:

```
public class ClasseGenericaTeste01 {  
    public static void main(String[] args) {  
        List<Carro> carrosDisponiveis = new ArrayList<>(  
                List.of(new Carro("BMW"), new Carro("Nissan")));  
  
        RentavelService<Carro> rentavelServiceCarro = new RentavelService<>(carrosDisponiveis);  
  
        Carro carro = rentavelServiceCarro.buscarVeiculosDisponiveis();  
        System.out.println("Usando carro por 1 mês...");  
        rentavelServiceCarro.retornarVeiculoAlugado(carro);  
  
    }  
}
```