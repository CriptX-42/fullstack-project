---
Created: 2025-03-16
---
### Significado
Em vez de classes tradicionais usadas em `java` por exemplo, o js consegue herdar propriedades e métodos de outros objetos

Isso tudo é feito através do `prototype`, que é um outro objeto do qual ele pode herdar tudo.

 
### Vamos ao passo a passo
- Você pode criar um objeto com um prototipo explicito (usando o `objetct.create`):

```
const animal = {
  fazerSom() {
    console.log("Som genérico de animal");
  }
};

const cachorro = Object.create(animal);
cachorro.fazerSom(); // Som genérico de animal

```

#### Usando o prototype em funções construturas:

```
function Pessoa(nome) {
  this.nome = nome;
}

Pessoa.prototype.dizerOi = function() {
  console.log(`Oi, meu nome é ${this.nome}`);
};

const pessoa1 = new Pessoa("Alice");
pessoa1.dizerOi(); // Oi, meu nome é Alice

```

#### Usando Class (ES6)

```
class Carro {
  constructor(modelo) {
    this.modelo = modelo;
  }

  buzinar() {
    console.log("Bii bip!");
  }
}

const meuCarro = new Carro("Fusca");
meuCarro.buzinar(); // Bii bip!

```