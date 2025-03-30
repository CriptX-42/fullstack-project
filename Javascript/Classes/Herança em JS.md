---
Created: 2025-03-30
---
Podemos criar classe que herda característica de outras usando `extends`:

```
class Estudante extends Pessoa {
  constructor(nome, idade, curso) {
    super(nome, idade); // Chama o construtor da classe pai
    this.curso = curso;
  }

  estudar() {
    return `${this.nome} está estudando ${this.curso}.`;
  }
}

const estudante1 = new Estudante("Carlos", 22, "Engenharia");
console.log(estudante1.apresentar()); // Herda método da classe Pessoa
console.log(estudante1.estudar());

```