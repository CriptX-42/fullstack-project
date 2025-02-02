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
    public static void calcularImpostoComputador(Computador computador) {  
        System.out.println("Relatório de imposto do computador");  
        double imposto = computador.calcularImposto();  
        System.out.println("Computador" + computador.getNome());  
        System.out.println("Valor do computador" + " " + computador.getValor());  
        System.out.println("Imposto a ser pago"  + " " + imposto);  
    }  
  
    public static void calcularImpostoTomate(Tomate tomate) {  
        System.out.println("Relatório de imposto do tomate");  
        double imposto = tomate.calcularImposto();  
        System.out.println("Computador" + tomate.getNome());  
        System.out.println("Valor do tomate"  + " " + tomate.getValor());  
        System.out.println("Imposto a ser pago"  + " " + imposto);  
    }  
}
```

View :
==Referenciando o menos especifico no mais especifico===
```
public static void main(String[] args) {  
    Produto computador = new Computador("Predator", 2000.00);  
    Produto tomate = new Tomate("Tumate", 20.00);  
    CalculadoraImposto.calcularImpostoComputador(computador);  
    System.out.println("-----------------------------------");  
    CalculadoraImposto.calcularImpostoTomate(tomate);  
}
```

Diagrama do cast
![[Java/Orientação a Objetos/OO/Polimorfismo/images/Untitled Diagram 1.svg]]