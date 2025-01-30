---
Created: 2025-01-30
---

> [!NOTE] Regras
> Numa interface todos os atributos são constantes (static e final)
> E podemos adicionar métodos estáticos, nunca vão ser sobrescritos


Exemplo de uso: 

```
public interface DataLoader {  
	int MAX_DATA_SIZE = 10 // Isso é publico, estatico e final
	void load();

	static void retriveMaxDataSize() { //Isso é publico
		sysout("Qualquer coisa")
	}
}
```

> Podemos chamar isso nas classes filhas mas não podemos sobrescrever