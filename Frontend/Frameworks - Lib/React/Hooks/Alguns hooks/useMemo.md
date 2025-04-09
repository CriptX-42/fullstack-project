---
Created: 2025-04-08
tags:
  - Aprofundar
Creatd:
---
### Definição
É o tipo mais primitivo do `React.memo`, mas não memoriza componente, mas sim o resultado de uma função

```
const valorMemorizado = useMemo(() => {
  // lógica pesada
  return resultado;
}, [dependencias]);

```

### ✅ Quando usar?

Use `useMemo` para:

- **Evitar cálculos pesados desnecessários.**
    
- **Evitar recriação de objetos ou arrays** (ex: para evitar re-render de filhos com `React.memo`).
    
- **Melhorar performance** em renderizações complexas.


### Exemplo simples
```
const numeros = [1, 2, 3, 4];

const soma = useMemo(() => {
  console.log("Calculando soma...");
  return numeros.reduce((acc, n) => acc + n, 0);
}, [numeros]);

return <p>Soma: {soma}</p>;

```


> [!Danger] Cuidado
> Se a logica for pesada, talvez não valha a pena


