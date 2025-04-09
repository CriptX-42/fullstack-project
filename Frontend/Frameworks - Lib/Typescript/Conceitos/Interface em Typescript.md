---
Created: 2025-04-09
---
------

### Merge declaration

Imagine que existe o seguinte cenario:

```
interface Pessoa {
name: string;
}

interface Pessoa {
age: number
}
const pessoa: Pessoa = {

}
```

	Esse código dara erro, mas não por estar faltando nome OU age no objeto pessoa. mas sim pq ele exige que pessoa receba os dois em seu objeto

- Exemplo:

```
interface Pessoa {
name: string;
}

interface Pessoa {
age: number
}

const pessoa: Pessoa = {
name: 'Ricardo',
age: 27
}
```


### Keyof
- Não consigo transformar um tipo em outro mas posso usar o generics

### Outras coisas

- Não consigo fazer isso em interface
```
// É string é um alias de email
type Email = string

function sendEmail(email: Email) {}
```