---
Created: 2025-02-02
---
Ela pega variáveis de tipo primitivos e transforma em objetos encapsulados: 

#### Exemplo de um tipo *Autoboxing*

| Tipo      | valor |
| --------- | ----- |
| Byte      | 1     |
| Short     | 1     |
| Integer   | 1     |
| Long      | 10L   |
| Float     | 10F   |
| Double    | 10D   |
| Character | "W"   |
| Boolean   | false |

> [!NOTE] Um adendo
> Agora essas variavies estão associadas a um tipo de polimorfismo, não a uma simples variável: 
[^1]![[Pasted image 20250202180918.png]]



> [!Warning] Estrutura de dados
> Quando trabalhamos com *arrayList*, *vetores* ou *collections*. Eles não trabalham com tipos primitivos. Pois dentro das coleções você trabalha com **referencias**

[^1]: Anatomia de um tipo primitivo "Byte"


#### Exemplo de um tipo **Unboxing**

```
Integer intWrapper = 1;

int i = intWrapper;
```

O java facilita você converter um wreapper numa variável primitiva 