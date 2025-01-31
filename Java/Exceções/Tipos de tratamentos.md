---
Created: 2025-01-30
---
#### Utilizando o throw new

```
public class Test {  
    public static void main(String[] args) {  
        System.out.println(divisao(1, 0));  
    }  
  
    private static int divisao(int a, int b) {  
        if(b == 0){  
            throw new IllegalArgumentException("Não pode fazer divisão por 0");  
        }  
        return a/b;  
    }  
}
```


> [!Error] Saída
> Exception in thread "main" java.lang.IllegalArgumentException: Não pode fazer divisão por 0
at OException.Runtime.Test.divisao(Test.java:10)
at OException.Runtime.Test.main(Test.java:5)


### Uma forma mais simples de tratamento 

```
public class Exception01 {  
    public static void main(String[] args) throws IOException {  
        criarNovoArquivo();  
    }  
  
    public static void criarNovoArquivo() throws IOException {  
	    File file = new File("/home\\teste.txt");  
         boolean criado = file.createNewFile();  
         System.out.println("Arquivo criado " + criado);  
    }  
}
```

> Eu obrigo o método **main** a abstrair e tratar a exceção

#### Lançando uma exceção dentro do tryCatch

```
public class Exception01 {  
    public static void main(String[] args) {  
        criarNovoArquivo();  
    }  
  
    private static void criarNovoArquivo() {  
    File file = new File("/home\\teste.txt");  
        try {  
         boolean criado = file.createNewFile();  
         System.out.println("Arquivo criado " + criado);  
        }catch (IOException exception){  
            exception.printStackTrace();  
            throws new RuntimeException("Problemas na hora de criar o arquivo")
        }  
    }  
}
```