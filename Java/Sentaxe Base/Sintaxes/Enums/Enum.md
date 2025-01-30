---
Created: 2024-01-29
---

> [!NOTE] Conceito
> Funciona como uma coleção de atributos embargadas por *constante* e *static* e *final* ou seja, não podem ser alterados. ==Buscar definição melhor==

```
public enum TipoCliente {
	PESSOA_FISICA,
	PESSOA_JURIDICA
}
```

Podemos também criar dentro e uma classe comum:
```
public class Cliente {
	public enum TipoCliente {
		PESSOA_FISICA,
		PESSOA_JURIDICA
	}
	// MAS AINDA PRECISAMOS COLOCAR ISSO DENTRO DE UM ATRIBUTO: 
		private TipoCliente tipoCliente;
}
```


> Como inserir um valor no meus atributos de enum?


==Se inserir direto no enum ele da erro, pois ele entende que estamos passando dois valores ao construtor (já pré criado do java)==

```
public enum TipoCliente {
	PESSOA_FISICA(1),
	PESSOA_JURIDICA(2);

	public int valor;

	public TipoCliente(int valor){
		this.VALOR = valor
	}

	public int getValor() {
		return valor
	}
}

```

> Também podemos fazer isso de uma forma composta. Ex:

```
public enum TipoCliente {
	PESSOA_FISICA(1, "Pessoa física"),
	PESSOA_JURIDICA(2, "Pessoa Jurídica");

	public int VALOR;
	public String nomeRelatorio;

	public TipoCliente(int valor, string nomeRelatorio){
		this.VALOR = valor
		this.nomeRelatorio = nomeRelatorio;
	}

	public int getValor() {
		return valor
	}
	public int getNomeRelatorio() {
		return nomeRelatorio
	}
}

```



> [!NOTE] E temos mais...
> [[Busca por atributos]]
