---
Created: 2025-02-10
---

### Trabalhando com polimorfismo sem listas (o problema)

Imagine que temos o seguinte código fazendo o uso do ***Polimorfismo***:

```
abstract class Animal {  
    abstract void consulta();  
}  
  
class Cachorro extends Animal {  
    @Override  
    void consulta() {  
        System.out.println("Consultando cachorro");  
    }  
}  
  
class Gato extends Animal {  
    @Override  
    void consulta() {  
        System.out.println("Consultando Gato");  
    }  
}  
  
public class WildCardsTeste01 {  
  
    public static void main(String[] args) {  
         Cachorro[] cachorro = {new Cachorro(), new Cachorro()};  
         Gato[] gato = {new Gato(), new Gato()};  
        printCunsulta(cachorro);  
        printCunsulta(gato);  
  
    }  
    private static void printCunsulta(Animal[] animals) {  
        for (Animal animal : animals) {  
            animal.consulta();  
        }  
  
    }  
}
```


> [!Example] Saída
```
Consultando cachorro
Consultando cachorro
Consultando Gato
Consultando Gato
```


Podemos criar uma lista de cachorro e gato, lidar com isso no java é simples, mas ao alterarmos essa lista no método printCunsulta pode ser até uma quebra de código, exemplo:

```
private static void printCunsulta(Animal[] animals) {  
    for (Animal animal : animals) {  
        animal.consulta();  
    }  
  
    animals[1] = new Gato();  
  
}
```


> [!Example] Saída
```
Consultando cachorro
Consultando cachorro
Exception in thread "main" java.lang.ArrayStoreException: ZGenerics.Test.Gato
	at ZGenerics.Test.WildCardsTeste01.printCunsulta(WildCardsTeste01.java:35)
	at ZGenerics.Test.WildCardsTeste01.main(WildCardsTeste01.java:26)
```

> E ainda conseguimos trabalhar com esse conceito num **Array** mas uma **Lista** é totalmente diferente


### Agora vamos trabalhar com listas

#### O subproblema
- Imagine que vamos simplificar e resolver nossa vida com uma Lista. Com o seguinte código:

```
public class WildCardsTeste02 {  
  
    public static void main(String[] args) {  
        List<Cachorro> cachorros = List.of(new Cachorro(), new Cachorro());  
        List<Gato> gatos = List.of(new Gato(), new Gato());  
  
        printCunsulta(cachorros);  
    }  
    private static void printCunsulta(List<Animal> animals) {  
        for (Animal animal : animals) {  
            animal.consulta();  
        }  
    }  
}
```

Obtemos o seguinte erro:
![[Pasted image 20250210161816.png]]

> Por conta do **Type Erasure** o java não sabe em tempo de compilação que uma lista de cachorros pode ser referenciada  a uma lista de *animais*

E ainda podemos fazer isso:

```
private static void printCunsulta(List<Animal> animals) {  
    for (Animal animal : animals) {  
        animal.consulta();  
    }  
    animals.add(new Cachorro());  
}
```

- Pois dentro da referencia **animal** podemos ter um cachorro

#### Agora, como podemos fazer o método printCunsulta aceitar uma classe quem extende animal? 

- Basta fazer isso: 

==Estamos falando que aceitamos qualquer tipo de Lista que extende *Animal*== ou seja, qualquer animal ou  **filho** de animal
```
private static void printCunsulta(List<? extends Animal> animals) {  
    for (Animal animal : animals) {  
        animal.consulta();  
    }  
}
```


> [!Warning] Dois pontos importantes
> 1. Não podemos adicionar elementos nessa lista depois de assinar esse contrato
> 2. Independente se *Animal* por exemplo é um interface ou não, devemos utilizar **Extends** na tipagem do parametro

Então essa é a saída:


> [!Example] Saída
```
Consultando cachorro
Consultando cachorro
Consultando Gato
Consultando Gato
```

#### Mas e se for uma necessidade a dição de algum item na nossa lista?

Basta colocarmos que queremos receber qualquer um que seja *animal* ou qualquer classe que seja pai:

> super Animal pode ser super Cachorro ou super Gato, não faz tanta diferença...

```
private static void printCunsulta(List<? super Animal> animals) {  
    for (Object animal : animals) {  
        if( animal instanceof Cachorro);  
    }  
}
```

Estamos usando o mais genérico para representar o animal, igual no exemplo acima (**sem lista**)

- Aqui podemos adicionar usando a garantia do polimorfismo:

```
private static void printCunsulta(List<? super Animal> animals) {  
    animals.add(new Cachorro());  
    animals.add(new Gato());  
      
}
```

Temos a garantia de que mesmo o mais genérico, ainda é um animal. Mas com um contrato mais flexivel, isso não significa um contrato melhor 