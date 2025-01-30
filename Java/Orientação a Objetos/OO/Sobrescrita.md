---
Created: 2025-01-29
---

> [!NOTE] Pra que usarmos?
> Uma forma de sobrescrita do extensão *object* (por default já importada em nossas classes).
> Podemos sobrescrever e retornar o que quiser nelas

 - Um exemplo:
 
```
 public class Pessoa {  
    public String nome;  
  
    @Override  // para garantir a sobrescrita
    public String toString(){  
        return "Pessoa" + " " + this.nome;  
    }  
  
    public Pessoa(String nome) {  
        this.nome = nome;  
    }  
  
    public String getNome() {  
        return nome;  
    }  
  
    public void setNome(String nome) {  
        this.nome = nome;  
    }  
}
```

toString é a extensão do *object*:

![[Pasted image 20250129171853.png]]

 - Uso:
```
 public static void main(String[] args){  
    Pessoa pessoa = new Pessoa("Ricardo");  
  
    System.out.println(pessoa);  
}

Saída: 
Pessoa Ricardo
```