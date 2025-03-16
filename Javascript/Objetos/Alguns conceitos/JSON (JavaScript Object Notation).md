---
Created: 2025-03-16
---
### Definição rápida
Um formato leve de troca de dados baseado em textos. Ele é fácil para humanos e simples para maquinas e é amplamente usado para transmissão de dados entre servidor/cliente em APIs

```
{
  "nome": "João",
  "idade": 30,
  "casado": true,
  "filhos": ["Ana", "Carlos"],
  "endereco": {
    "rua": "Rua das Flores",
    "numero": 123
  }
}

```

### Conversões

🔹 Converter um objeto JavaScript para JSON:

```
const obj = { nome: "João", idade: 30 };
const jsonString = JSON.stringify(obj);
console.log(jsonString); // '{"nome":"João","idade":30}'

```

🔹 Converter JSON para um objeto JavaScript:

```
const jsonString = '{"nome":"João","idade":30}';
const obj = JSON.parse(jsonString);
console.log(obj.nome); // João

```
