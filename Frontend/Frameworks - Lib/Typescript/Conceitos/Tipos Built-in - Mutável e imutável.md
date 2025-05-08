---
Created: 2025-05-01
---
---

Tipos embutidos são tipos já fornecidos pela linguagem e pela biblioteca padrão do javascript,Aqui está uma visão geral dos Built-in:

📦 **Tipos Primitivos (Primitive Types)**
- string
- number
- boolean
- bigint (inteiros muito grandes)
- sybol
- null
- undefined

🔢 **Tipos Literais**
Valores fixos que um tipo pode assumir.
``` typescript
const direcao: "esquerda" | "direita" = "esquerda";
```

🧱 **Tipos Estruturais**
- `object`: representa qualquer valor que não seja primitivo.
- `Array<T>` ou `T[]`: listas de elementos.
- `Tuple`: array com tipos fixos e ordem específica:
```typescript
const tupla: [string, number] = ["idade", 30];
```

### ⚙️ **Tipos Funcionais**

- `Function`: tipo genérico de função (não recomendado usar diretamente).

```typescript
const func: Function = () => {};
```

### 🧠 **Tipos Avançados Built-in (utility types)**

Estes vêm do próprio TypeScript, não do JavaScript:

- `Partial<T>`: torna todas as propriedades opcionais.
- `Required<T>`: torna todas obrigatórias.
- `Readonly<T>`: propriedades somente leitura.
- `Record<K, T>`: cria objeto com chaves `K` e valores do tipo `T`.
- `Pick<T, K>` / `Omit<T, K>`: pega ou omite propriedades de um tipo.

✅ **Tipos Primitivos**

São tipos **imutáveis** e armazenados **por valor**. Isso significa que, ao atribuí-los a uma variável ou passá-los para uma função, o valor em si é copiado.

🧱 **Tipos Não Primitivos**
São mutáveis e tem armazenamento por referencia, ou seja, armazena um endereço em memória, não salva o valor em sí. Se temos 2 varáveis apontando para o mesmo objeto, mudar uma afeta a outra:
``` typescript
const obj1 = { nome: "Maria" };
const obj2 = obj1;

obj2.nome = "João";

console.log(obj1.nome); // "João" (ambos apontam para o mesmo objeto)

```

|Característica|Primitivo|Não Primitivo|
|---|---|---|
|Armazenamento|Por valor|Por referência|
|Mutabilidade|Imutável|Mutável|
|Exemplos|`string`, `number`, `boolean`|`object`, `array`, `function`|
|Comparação (`===`)|Compara valor direto|Compara referências|
