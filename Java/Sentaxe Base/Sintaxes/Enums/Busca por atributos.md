---
Created: 2025-01-30
---


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

E queremos buscar exatamente se o cliente é **Pessoa fisica** ou **Pessoa juridca**  pelos atributos. Então basta fazer: 

```
public enum TipoCliente {
	PESSOA_FISICA(1, "Pessoa física"),
	PESSOA_JURIDICA(2, "Pessoa Jurídica");

	public static TipoCliente tipoClientePorNomeRelaorio(String nomeRelatorio) {
		for (TipoCliente tipoCliente: values()) {
			if(tipoCliente.getNomeRelatorio().equals(nomeRelatorio)) {
				return tipoCliente
			}
			return null
		}
	}
	...

```

> **values()** vai retornar um array de todo o TipoCliente
