---
Created: 2025-02-02
---
- Exemplo de uso

```
public static void main(String[] args) {  
    Calendar calendar = Calendar.getInstance(); // é uma classe abstrata por isso não precisamos do new  
    Date date = calendar.getTime();  
    System.out.println(date);  

	Saída
	----------
	Sun Feb 02 21:09:35 BRT 2025
}
```