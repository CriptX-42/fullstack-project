---
Created: 2025-01-29
---

> [!NOTE] Pra que serve
> Uma forma de chumbar um valor numa variável e não fazer ela mudar nunca
> Ela deve ser escrita em letras maiúsculas e separados por "_"

- Exemplo de uso:
```
public final double VALOR_DE_PI = 3.14;
//ou
public static final double VALOR_DE_PI = 3.14;
```

Quando eu não quiser que minha classe seja estendida: 
```
public final class Carro{
	....
}
```

> O mesmo vale pra não sobrescrita de métodos dentro da minha classe

```
public final class Carro{
	// não permite sobrescrever esse método caso minha classe seja estendida
	public final void imprime() {
	
	}
}
```