---
Created: 2025-01-29
tags:
---

> [!NOTE] O que é?
> É o relacionamento entre dois objetos

#### Unidirecional 1:1
	Um exemplo de associação unidirencional

Um time
```
public class Time {  
    private String nome;  
  
    public Time(String nome) {  
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

Um jogador associado a um time
```
public class Jogador {  
    private String nome;  
    private Time time;  
  
    public Jogador(String nome) {  
        //Caso eu torne o time obrigatório, basta adicionar ao construtor  
        this.nome = nome;  
    }  
  
    public void imprime() {  
        if(time != null) {  
            System.out.println(this.nome);  
            System.out.println(time.getNome());  
        }  
    }  
  
    public Time getTime() {  
        return time;  
    }  
  
    public void setTime(Time time) {  
        this.time = time;  
    }  
  
    public String getNome() {  
        return nome;  
    }  
  
    public void setNome(String nome) {  
        this.nome = nome;  
    }  
}
```

O uso e inserção de dados 1:1
```
public static void main(String[] args){  
    Jogador jogador1 = new Jogador("Ricardo");  
    Jogador jogador2 = new Jogador("Neymar");  
  
    Time time = new Time("Palmeiras");  
    Time time2 = new Time("Santos");  
  
    jogador2.setTime(time2);  
    jogador1.setTime(time);  
  
    jogador1.imprime();  
    
    Saída:
    -------------
    Ricardo
    Palmeiras
}
```


#### Multidirecional 1:n
```
public class Professor {  
    private String nome;  
  
    public Professor(String nome) {  
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

```
public class Escola {  
    private String nome;  
    private Professor[] professores;  
  
    public Escola(String nome, Professor[] professores) {  
        this.nome = nome;  
        this.professores = professores;  
    }  
  
    public  void imprime() {  
        if (professores == null) return;  
        System.out.println(this.nome);  
        for (Professor professor : professores) {  
            System.out.println(professor.getNome());  
        }  
  
    }  
  
    public String getNome() {  
        return nome;  
    }  
  
    public void setNome(String nome) {  
        this.nome = nome;  
    }  
  
    public Professor[] getProfessores() {  
        return professores;  
    }  
  
    public void setProfessores(Professor[] professores) {  
        this.professores = professores;  
    }  
}
```

```
public static void main(String[] args){  
    Professor professor = new Professor("Teste da Silva");  
    Professor professor2 = new Professor("Teste da Silva2");  
    Professor professor3 = new Professor("Teste da Silva3");  
    Professor[] professores = {professor, professor2, professor3};  
    Escola escola = new Escola("Escola teste", professores);  
  
    escola.imprime();  
}
Saída:
----------------
Escola teste
Teste da Silva
Teste da Silva2
Teste da Silva3

```

#### Relacionamento bidirecional n:n
```
public class Time {  
    private String nome;  
    private Jogador[] jogadores;  
  
    public Time(String nome) {  
        this.nome = nome;  
    }  
  
    public Time(Jogador[] jogadores) {  
        this.jogadores = jogadores;  
    }  
  
    public void imprime() {  
        if(jogadores == null) return;  
        System.out.println(this.nome);  
  
        for (Jogador jogador : jogadores) {  
            System.out.println(jogador.getNome());  
        }  
    }  
  
    public Jogador[] getJogadores() {  
        return jogadores;  
    }  
  
    public void setJogadores(Jogador[] jogadores) {  
        this.jogadores = jogadores;  
    }  
  
    public String getNome() {  
        return nome;  
    }  
  
    public void setNome(String nome) {  
        this.nome = nome;  
    }  
}

```

```
public class Jogador {  
    private String nome;  
    private Time time;  
  
    public Jogador(String nome) {  
        //Caso eu torne o time obrigatório, basta adicionar ao construtor  
        this.nome = nome;  
    }  
  
    public void imprime() {  
        if(time != null) {  
            System.out.println(this.nome);  
            System.out.println(time.getNome());  
        }  
    }  
  
    public Time getTime() {  
        return time;  
    }  
  
    public void setTime(Time time) {  
        this.time = time;  
    }  
  
    public String getNome() {  
        return nome;  
    }  
  
    public void setNome(String nome) {  
        this.nome = nome;  
    }  
}
```

```
public static void main(String[] args){  
    Jogador jogador = new Jogador("Cafu");  
    Time time = new Time("Brasil");  
  
    Jogador[] jogadores = {jogador};  
  
    jogador.setTime(time);  
  
    time.setJogadores(jogadores);  
  
    System.out.println("-----------Jogador-------------");  
    jogador.imprime();  
    System.out.println("------------TIME-------------");  
    time.imprime();  
}

Saída: 
-----------Jogador-------------
Cafu
Brasil
------------TIME-------------
Brasil
Cafu
```