---
Created: 2025-02-05
---

> [!NOTE] Igualdade solta `==`
> Um modo de comparar dois valores sem se preocupar com os tipos de dados
> Se um deles forem diferentes, tenta fazer a conversão de um para fazer a comparação
> 

```
console.log(5 == '5'); // true (conversão implícita)
console.log(true == 1); // true (true é convertido para 1)
console.log(null == undefined); // true
```



> [!NOTE] Igualdade estrita `===`
> Compara os valores sem fazer a conversão

```
console.log(5 === '5'); // false (tipos diferentes: number e string)
console.log(true === 1); // false (tipos diferentes: boolean e number)
console.log(null === undefined); // false (tipos diferentes)

```

