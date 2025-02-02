---
Created: 2025-02-02
---

> [!Note] Imagine o problema
> Temos a leitura de um arquivo e temos que fechar nosso reader depois de ler um arquivo, usando o *finally* porem esse fechamento necessita de um try/catch

Código bem feio:
```
public static void LerArquivo2() {  
    Reader reader = null;  
    try {  
        reader = new BufferedReader(new FileReader("teste.txt"));  
    }catch (FileNotFoundException e) {  
        e.printStackTrace();  
    }finally {  
        try {  
            reader.close();  
        } catch (IOException e) {  
            throw new RuntimeException(e);  
        }  
    }  
}
```

Try com recursos. Na linha do try ele está se encarregando de fechar todo o escopo do reader:

> Mas só podemos implementar objetos ou variavas de referencia no Resources caso elas implementem a interface *Readable* ou *Closeable*:

![[Pasted image 20250202135415.png]]

```
public static void LerArquivo2() throws IOException {  
    try (Reader reader  = new BufferedReader(new FileReader("teste.txt"))) {  
  
    }catch (FileNotFoundException e) {  
        e.printStackTrace();  
    }  
}
```