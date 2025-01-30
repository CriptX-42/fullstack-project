---
Created: 2025-01-30
---
> Vamos calcular imposto sobre produtos: 

- Pacote de domínio

Interface:
```
public interface Taxavel {  
    double calcularImposto();  
}
```

Produto (superclasse):
```
public class Produto implements Taxavel {  
    protected String nome;  
    protected Double valor;  
  
    public Produto(String nome, Double valor) {  
        this.nome = nome;  
        this.valor = valor;  
    }  
  
    @Override  
    public double calcularImposto() {  
        return 0;  
    }  
  
    public String getNome() {  
        return nome;  
    }  
  
    public Double getValor() {  
        return valor;  
    }  
}
```

Subclasses de produto:

```
public class Tomate extends Produto {  
    public static final double IMPOSTO_POR_CENTO = 0.06;  
  
    public Tomate(String nome, Double valor) {  
        super(nome, valor);  
    }  
  
  
    @Override  
    public double calcularImposto() {  
        System.out.println("Calculando imposto do tomate");  
        return this.valor * IMPOSTO_POR_CENTO;  
    }  
  
  
}
```


```
public class Computador extends Produto{  
  
  
    public static final double IMPOSTO_POR_CENTO = 21;  
  
    public Computador(String nome, Double valor) {  
        super(nome, valor);  
    }  
  
  
    @Override  
    public double calcularImposto() {  
        System.out.println("Calculando imposto do computador");  
        return this.valor * IMPOSTO_POR_CENTO;  
    }  
  
}
```


Serviço (Regra de negócios):

```
public class CalculadoraImposto {  
  
    // se não tiver acessando nenhum atributo de classe vc pode transformar os métodos em estatico  
    // para não estanciarmos na view  
  
    public static void calcularImposto(Produto produto) {  
        System.out.println("Relatório de imposto do produto");  
        double imposto = produto.calcularImposto();  
        System.out.println("Computador" + produto.getNome());  
        System.out.println("Valor do produto"  + " " + produto.getValor());  
        System.out.println("Imposto a ser pago"  + " " + imposto);  
    }  
}
```

View :
```
public static void main(String[] args) {  
    Computador computador = new Computador("Predator", 2000.00);  
    Tomate tomate = new Tomate("Tumate", 20.00);  
    CalculadoraImposto.calcularImposto(computador);  
    System.out.println("-----------------------------------");  
    CalculadoraImposto.calcularImposto(tomate);  
}
```