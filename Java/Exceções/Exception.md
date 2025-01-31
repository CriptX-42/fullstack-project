---
Created: 2025-01-31
---
Exemplo de exception: 

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
        }  
    }  
}
```


> [!Error]  Saída na nossa stack trace
> java.io.IOException: Permissão negada
at java.base/java.io.UnixFileSystem.createFileExclusively0(Native Method)
at java.base/java.io.UnixFileSystem.createFileExclusively(UnixFileSystem.java:258)
at java.base/java.io.File.createNewFile(File.java:1045)
at OException.Exception.Exception01.criarNovoArquivo(Exception01.java:14)
at OException.Exception.Exception01.main(Exception01.java:8)

