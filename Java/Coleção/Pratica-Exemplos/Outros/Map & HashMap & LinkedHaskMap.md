---
Created: 2025-02-08
---

> [!NOTE] Algumas observações
> Map não faz parte da linha de herança da *collection*
> Sempre vai trabalhar com chave (k) e valor (v)

- Exemplo simples de uso

```
public static void main(String[] args) {  
    Map<String, String> map = new HashMap<>();  
    map.put("keyboard","teclado");  
    map.put("mose","mouse");  
  
    System.out.println(map);  
    System.out.println();  
  
    for (String key: map.keySet()) {  
        System.out.println(key + " " + map.get(key));  
    }  
  
    System.out.println();  
  
    for (String values: map.values()) {  
        System.out.println(values);  
  
    }  
  
}
```


> [!Example] Saída
```
{keyboard=teclado, mose=mouse}

keyboard teclado
mose mouse

teclado
mouse
```



> [!Warning] Podemo melhorar
> Podemos trocar o `Map<String, String> map = new HashMap<>();` por `Map<String, String> map = new LinkedHashMap<>();`. Assim vamos ter nosso map baseado na ordem de **inserção**
