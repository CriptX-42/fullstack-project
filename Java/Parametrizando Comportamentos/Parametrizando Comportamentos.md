---
Created: 2025-02-12
---

> [!Danger] O problema
> Imagine que temos um objeto carro, e queremos fazer um filtro por cor, outro filtro por ano do carro. Na nossa logica ingenua, ficaria assim:

```
public class Car {  
    private String name = "Audi";  
    private String color;  
    private int year;  
  
    public Car( String color, int year) {  
        this.color = color;  
        this.year = year;  
    }  
  
    @Override  
    public String toString() {  
        return "Car{" +  
                "name='" + name + '\'' +  
                ", color='" + color + '\'' +  
                ", year=" + year +  
                '}';  
    }  
  
...
}
```


- Nosso uso:
```
public class ComportamentoPorParametro {  
    private static List<Car> cars = List.of(new Car("green", 2011),  
            new Car("black", 1998),  
            new Car("red", 2019));  
  
    public static void main(String[] args) {  
        System.out.println(filterByColor(cars, "green"));  
        System.out.println(filterByYear(cars, 2000));  
    }  
  
    private static List<Car> filterByColor(List<Car> cars, String cor) {  
        List<Car> filterCar = new ArrayList<>();  
        for (Car car : cars) {  
            if(car.getColor().equals(cor)) {  
                filterCar.add(car);  
            }  
        }  
        return filterCar;  
    }  
  
    private static List<Car> filterByYear(List<Car> cars, int year) {  
        List<Car> filterCar = new ArrayList<>();  
        for (Car car : cars) {  
            if(car.getYear() <= year) {  
                filterCar.add(car);  
            }  
        }  
        return filterCar;  
    }  
}
```

> Como é notável, estamos duplicando os métodos e os if's, como resolver isso implicando em um if só? e só um método?

### Usando função anonima, interfaces e polimorfismo

Ao criarmos uma interface:

```
public interface CarPredicate {  
    boolean test(Car car);  
}
```

- O uso dela de maneira mais simples:
```
public class ComportamentoPorParametro02 {  
    private static List<Car> cars = List.of(new Car("green", 2011),  
            new Car("black", 1998),  
            new Car("red", 2019));  
  
    public static void main(String[] args) {  
        List<Car> greenCars  = filter(cars, new CarPredicate() {  
            @Override  
            public boolean test(Car car) {  
                return car.getColor().equals("green");  
            }  
        });  
  
        System.out.println(greenCars);  
    }  
  
    private static List<Car> filter(List<Car> cars, CarPredicate carPredicate) {  
        List<Car> filterCar = new ArrayList<>();  
        for (Car car : cars) {  
           if(carPredicate.test(car)) {  
               filterCar.add(car);  
           }  
        }  
        return filterCar;  
    }  
}
```


> [!NOTE] O que mudou
> Criamos **greenCars** com uma função anonima, nos permitindo passar uma condicional como paramentro usando uma *interface* 

### Simplificando ainda mais com Lambda 

- Podemos usar o lambada para passar essa condição com a interface

```
public class ComportamentoPorParametro02 {  
    private static List<Car> cars = List.of(new Car("green", 2011),  
            new Car("black", 1998),  
            new Car("red", 2019));  
  
    public static void main(String[] args) {  
        List<Car> greenCars  = filter(cars, car -> car.getColor().equals("green"));  
        System.out.println(greenCars);  
    }  
  
    private static List<Car> filter(List<Car> cars, CarPredicate carPredicate) {  
        List<Car> filterCar = new ArrayList<>();  
        for (Car car : cars) {  
           if(carPredicate.test(car)) {  
               filterCar.add(car);  
           }  
        }  
        return filterCar;  
    }  
}
```


> [!Example] Saída
```
[Car{name='Audi', color='green', year=2011}]
```


### E duas vezes mais

Podemos usar o Predicate do java e um generics para receber o parametro
```
private static List<Car> filter(List<Car> cars, Predicate<Car> carPredicate) {  
    List<Car> filterCar = new ArrayList<>();  
    for (Car car : cars) {  
       if(carPredicate.test(car)) {  
           filterCar.add(car);  
       }  
    }  
    return filterCar;  
}
```

- E podemos ser mais gerico ainda, não vejo tanta vantagem nisso, mas podemos kkk
```
private static <T> List<T> filterGeneric(List<T> list, Predicate<T> carPredicate) {  
    List<T> filter = new ArrayList<>();  
    for (T element : list) {  
        if(carPredicate.test(element)) {  
            filter.add(element);  
        }  
    }  
    return filter;  
}
```