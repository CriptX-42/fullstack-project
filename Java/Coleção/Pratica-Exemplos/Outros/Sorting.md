---
Created: 2025-02-05
---

> [!Tip] Para melhor aproveitamento
> Para melhor aproveitamento do sort, é sempre bom consultar o artigo [[Complexidade Big-O]]


 - Exemplo simples de Sorting (Por ordem alfabetica):

```
public static void main(String[] args) {  
    List<String> jogos = new ArrayList<>(6);  
  
    jogos.add("Resident Evil 3: Nemesys");  
    jogos.add("Medal of Honor");  
    jogos.add("Contra");  
    jogos.add("Metal Slug");  
    jogos.add("Drive I");  
    jogos.add("GTA III");  
  
  
    Collections.sort(jogos);  
  
    System.out.println(jogos);  
}
```


> [!Example] Saída:
```
 [Contra, Drive I, GTA III, Medal of Honor, Metal Slug, Resident Evil 3: Nemesys]
```



