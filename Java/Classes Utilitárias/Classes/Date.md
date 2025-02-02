---
Created: 2025-02-02
---

> [!WARNING] Cuidado ao usar o date
> Cuidado pois existem muitos métodos legados dentro do **Date()** em java
> Quase ninguém usa **Date()** em sistemas modernos

```
public static void main(String[] args) {  
    Date date = new Date(1_000_000_000_000L); // CONTA O TEMPO A PARTIR DE MS E É LONG;  
    System.out.println(date); 

	Saída: 
	-----------------
	Sat Sep 08 22:46:40 BRT 2001
}
```

