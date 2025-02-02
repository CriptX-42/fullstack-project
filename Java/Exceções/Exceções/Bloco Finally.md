---
Created: 2025-02-02
---

> [!Warning] Funcionamento
> Você já usou isso varias vezes para fechar um recurso de banco de dados
> O *finally* sempre vai ser executado, mesmo se der certo ou errado nosso try/catch



```
public static void main(String[] args) {  
    try {  
        System.out.println("Teste");  
        throw new RuntimeException();  //forçando exceção
    }catch (Exception e) {  
        e.printStackTrace();  
    } finally {  
        System.out.println("Caiu no finally");  
    }  

Saída:
Teste
Caiu no finally
java.lang.RuntimeException
	at OException.Teste02.main(Teste02.java:7)
}
```


%% Podemos usar o try sem o catch mas com o finally %%
