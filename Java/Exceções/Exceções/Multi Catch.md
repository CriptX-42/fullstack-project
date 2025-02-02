---
Created: 2025-02-02
---
> [!Warning] Funcionamento
> Você já usou isso varias vezes para fechar um recurso de banco de dados
> O *finally* sempre vai ser executado, mesmo se der certo ou errado nosso try/catch
> Podemos também evitar o aninhamento de catch's trabalhando com apenas uma separação em pipe

Exemplo:
```
public static void main(String[] args) {  
    try {  
        throw new RuntimeException();  
    }catch (ArrayIndexOutOfBoundsException | IllegalArgumentException e) {  
        e.printStackTrace();  
    }  
}
```
