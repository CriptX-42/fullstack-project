---
Created: 2025-02-02
tags:
  - Construir
---

> [!NOTE] Um simples exemplo
> Como o Builder e o Buffer podem mexer com o pool de strings


```
public class StringTest01 {  
    public static void main(String[] args) {  
        String nome = "Ricardo";  
        nome.concat("Carvarlho");  
        System.out.println("Sem string builder: " + nome);  
        StringBuilder sb = new StringBuilder("Ricardo");  
        sb.append(" Carvalho").append(" Sobrenome");  
        System.out.println("Com string builder: " + sb);  
  
        sb.reverse();  
        sb.delete(0,3);  
  
        System.out.println("Brincando com builder: " + sb);  
  
    }  
  
  
}
```

```
Saída:

Sem string builder: Ricardo
Com string builder: Ricardo Carvalho Sobrenome
Brincando com string builder: nerboS ohlavraC odraciR
```