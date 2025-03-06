---
tags:
  - Construir
  - Dicionário
---
### Definição

Em Javascript, um objeto nada mais é do que uma estrutura de dados que armazena um informações. Na estrutura de pares **chave-valor**. Cada chave possui seu respectivo valor.


> [!Tip] Ler Mais em
> [[Cópias de Objetos]]

### Brincando com isso

 - Imagine que temos esse objeto
```
const pessoa = {
  nome: "João",
  idade: 30,
  profissao: "Desenvolvedor"
};

```

Sabemos que para acessar o valor `nome`, basta chamar ´pessoa.nome´. Mas quando isso é algo dinâmico, podemos fazer:

```
console.log(pessoa["profissao"]); // "Desenvolvedor"

const chave = "idade";
console.log(pessoa[chave]); // 30

```

- Podemos modificar:

```
pessoa.email = "joao@email.com"; // Adicionando nova propriedade
pessoa.idade = 31; // Modificando valor existente

console.log(pessoa);

```

- Deletar

```
delete pessoa.profissao;

console.log(pessoa); // Agora o objeto não tem mais a propriedade "profissao"

```

- Colocar uma função dentro:

```
const carro = {
  marca: "Toyota",
  modelo: "Corolla",
  ano: 2022,
  ligar: function () {
    console.log("O carro está ligado!");
  }
};

carro.ligar(); // "O carro está ligado!"

```

```
const usuario = {
  nome: "Alice",
  saudacao: () => console.log("Olá, " + usuario.nome)
};

usuario.saudacao(); // "Olá, Alice"

```

### Usando as propriedades Object

```
console.log(Object.keys(pessoa)); // ["nome", "idade", "email"]
console.log(Object.values(pessoa)); // ["João", 31, "joao@email.com"]
console.log(Object.entries(pessoa)); // [["nome", "João"], ["idade", 31], ["email", "joao@email.com"]]

```


