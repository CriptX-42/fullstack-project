---
tags:
  - Construir
  - Dicionário
Created: 2025-02-03
---
#### Iteração
[[Iteração, transformação e comparação]]

### Arrays 

Em javascript, é dinamico, pode apresentar quaisquer dados.

```
const numeros = [1, 2, 3, 4, 5];
const misto = [1, "texto", { chave: "valor" }, [6, 7, 8]]; // Qualquer tipo de dado

```

- Métodos
```
const arr = [10, 20, 30];

arr.push(40);    // Adiciona no final: [10, 20, 30, 40]
arr.pop();       // Remove do final: [10, 20, 30]
arr.unshift(5);  // Adiciona no início: [5, 10, 20, 30]
arr.shift();     // Remove do início: [10, 20, 30]

arr.map(x => x * 2);   // Retorna [20, 40, 60]
arr.filter(x => x > 15); // Retorna [20, 30]
arr.reduce((acc, x) => acc + x, 0); // Soma: 60

```

### Typed Arrays

Foram introduzidos para manipular dados binarios de forma eficiente. Usados quando trabalhamos com ==WebGL, arquivos, buffers de rede== e coisas de baixo nivel.


> [!NOTE] Principais diferenças 
> - Os Typed Arrays armazenam apenas **números** (int ou float).
> - O tamanho é **fixo** após a criação.
> - O uso de memória é mais eficiente.


- Criando um Typed Array

```
const buffer = new ArrayBuffer(8); // Cria um buffer de 8 bytes (64 bits)
const view = new Int32Array(buffer); // Visualização como Int32 (4 bytes por elemento)
view[0] = 42;
view[1] = 100; // OK: Cada número ocupa 4 bytes (2 elementos cabem no buffer)

console.log(view); // Int32Array(2) [42, 100]

```

- Convertendo um Array para um Typed Array

```
const normalArray = [10, 20, 30];
const typedArray = new Int16Array(normalArray);
console.log(typedArray); // Int16Array(3) [10, 20, 30]
```


> [!Danger] Pra que usar isso?
> Quando estivermos lidando com manipulação de arquivos, graficos ou comunicação binaria, Tuped Arrays são a melhor escolha
