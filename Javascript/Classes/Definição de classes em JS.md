---
Created: 2025-03-30
---
Em JS é uma forma de definir objetos e sua estrutura de maneira mais organizada e reutilizavel. Foi introduzida no ES6.

Sintaxe baica:

```
class Pessoa {
  constructor(nome, idade) {
    this.nome = nome;
    this.idade = idade;
  }

  apresentar() {
    return `Olá, meu nome é ${this.nome} e tenho ${this.idade} anos.`;
  }
}

const pessoa1 = new Pessoa("Alice", 30);
console.log(pessoa1.apresentar());
// Saída: Olá, meu nome é Alice e tenho 30 anos.

```

---------
Componentes (já sabemos como funfa):

1. Construtor
	- Método especial que é chamado automaticamente ao instanciar a classe
	- Responsável por iniciar os atributos da instancia
2. Método
	1. Função definida dentro da classe que podem ser chamadas no objeto criado (Qualquer coisa em JS é um objeto kkk)

