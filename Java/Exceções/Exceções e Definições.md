---
Created: 2025-01-31
tags:
  - Dicionário
---

> [!WARNING] Nota rápida
> Todas as exceções são um objeto da classe *Throwable*
> Um erro é algo que ocorre na JVM e você não vai poder recuperar em tempo de execução
> 


Existe um erro bem famoso que ocorre, isso ocorre por conta da recursividade. Exemplo:
```
public class StackOverflow {  
    public static void main(String[] args) {  
        recursividade();  
    }  
  
    public static void recursividade() {  
        recursividade();  
    }  
}
```


> [!Error] Erro
> Exception in thread "main" java.lang.StackOverflowError
at OException.StackOverflow.recursividade(StackOverflow.java:9)


#### RuntimeException e Exception

> [!warning] Dois termos muito importantes...
> Checked. São filhas da classe *Exception* e se não for tratada vai estourar em tempo de execução
> 
> Unchecked. São filhas da classe *RuntimeExceptions* e quase 100% das vezes o problema é você

![[Java/img/Untitled Diagram.svg]]

> Error não é uma exceção, ela é filha de Throwable

#### RuntimeException (exceções)
[[RuntimeException (Exceções)]]

#### Exception

[[Exception]]

### Tipos de tratamentos

[[Tipos de tratamentos]]

#### Finally
[[Bloco Finally]]
#### Catch

[[Multi Catch]]

#### Try with resources
[[Try with resources]]

#### Exceções customizadas

[[Exceções customizadas]]

### E mais

> [!NOTE] Sobrescrita
> Na sobrescrita de métodos nós não precisamos lançar exceções. Mas se por ventura lançarmos, podemos fazer isso mais de uma vez e a classe que irá consumir esse método sobrescrito também vai ter de trata-lo
> 
