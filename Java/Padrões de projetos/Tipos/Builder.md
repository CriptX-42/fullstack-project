---
Created: 2025-02-25
---

> [!NOTE] Pra que serve?
> Isso reduz e muito a complexidade de criação de instanciação de nossos objetos. Principalmente facilitando na instanciação, onde precisamos passar muitos parâmetros a um objeto apenas


### Exemplo

```
public class Pessoa {  
    private String nome;  
    private String sobrenome;  
    private String  userName;  
    private String email;  
  
    public Pessoa(String email, String userName, String sobrenome, String nome) {  
        this.email = email;  
        this.userName = userName;  
        this.sobrenome = sobrenome;  
        this.nome = nome;  
    }  
  
  
    public static final class PessoaBuilder {  
        private String nome;  
        private String sobrenome;  
        private String userName;  
        private String email;  
  
        public PessoaBuilder() {  
        }  
  
  
  
        public PessoaBuilder nome(String nome) {  
            this.nome = nome;  
            return this;  
        }  
  
        public PessoaBuilder sobrenome(String sobrenome) {  
            this.sobrenome = sobrenome;  
            return this;  
        }  
  
        public PessoaBuilder userName(String userName) {  
            this.userName = userName;  
            return this;  
        }  
  
        public PessoaBuilder email(String email) {  
            this.email = email;  
            return this;  
        }  
  
        public Pessoa build() {  
            return new Pessoa(email, userName, sobrenome, nome);  
        }  
    }  
}
```

- Uso
- 
```
public static void main(String[] args) {  
    Pessoa build = new Pessoa.PessoaBuilder()  
            .nome("Ricardo")  
            .sobrenome("Carvalho")  
            .email("ricardo-svc@live.com")  
            .userName("Criptx-42")  
            .build();    
}
```



> [!Warning]  Para que serve o .build?
> Nos ajuda na imutabilidade (caso ela for desejada)
> Para seguir passo a passo a criação e passagem de valores para o objeto

