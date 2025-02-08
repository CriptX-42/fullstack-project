---
Created: 2025-02-04
tags:
  - Dicionário
---

> [!NOTE] Algumas peculiaridades
> Lista é uma interface
> **NÃO CRIAMOS LISTA COM TIPO PRIMITIVOS, SÓ WRAPPERS**


> [!tip] Subtópicos
>  1. [[Sorting]]
>  2. Sorting Customizado: 
> 	 1. [[Comparable]]
> 	 2. [[Comparator]]
> 	 3. [[Binary Search]]
> 	 4. [[Convertendo Lista&Array]]
> 	 5. [[iterator (exemplo de remoção)]]
> 	 6. [[Set&HashSet]]
> 	 7. [[NavigableSet&TreeSet]]
> 	 8. 


- Um exemplo usando Array List:


> [!Warning] Alguns cuidados
> Depois do list, colocamos um tipo no <> (diamond). 
> Dentro do *ArrayList*, temos capacidade dele, é opcional, mas muito bom por
> Para pegar o tamanho dos da lista usamos o **size()** e para pegar um indice usamos o **get()** quando se trata de *ArrayList* 


```
public static void main(String[] args) {  
    List<String> nomes = new ArrayList(16); //initialCapacity é opcional  
    nomes.add("Ricardo");  
    nomes.add("Teste");  
  
    for (String nome: nomes ) {  
        System.out.println(nome);  
    }  
  
    System.out.println("=====================");  
  
    for (int i = 0; i < nomes.size() ; i++) {  
        System.out.println(nomes.get(i));  
  
    }  
  
}
```

#### E mais 

Um exemplo de mais usos com list: 

- Imagine o seguinte código

```
public class SmartphoneTestList01 {  
    public static void main(String[] args) {  
  
        Smartphone s1 = new Smartphone("123", "Samsung");  
        Smartphone s2 = new Smartphone("123456", "Samsung");  
        Smartphone s3 = new Smartphone("789654", "Samsung");  
  
        List<Smartphone> smartphones = new ArrayList(6);  
        smartphones.add(s1);  
        smartphones.add(s3);  
        smartphones.add(s3);  
  
        for (Smartphone smartphone: smartphones) {  
            System.out.println(smartphone.toString());  
        };  
  
		Smartphone{serialNumber='123', marca='Samsung'}
		Smartphone{serialNumber='789654', marca='Samsung'}
		Smartphone{serialNumber='789654', marca='Samsung'}
    }  
}
```

 - Para executar o *equals* de maneira velada e achar um objeto na nossa lista:

```
Smartphone s4 = new Smartphone("789654", "Samsung");  
  
// Aqui o Equals vai ser executado  
System.out.println(smartphones.contains(s4));

======================
Saída: 
True
```


- Para achar um index e buscar um objeto pelo index:

```
int indexSmartphone = smartphones.indexOf(s4);  
  
System.out.println(indexSmartphone + " index");  
  
System.out.println(smartphones.get(indexSmartphone) + " Pegando pelo index");

===========================================
Saída:
1 index
Smartphone{serialNumber='789654', marca='Samsung'} Pegando pelo index
```



![[Pasted image 20250208180353.png]]