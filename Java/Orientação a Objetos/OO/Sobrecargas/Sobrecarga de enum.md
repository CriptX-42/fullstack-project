---
Created: 2025-01-30
---
> Podemos também inserir uma [[Sobrecarga]] dentro de um enum. Segue o exemplo: 


```
public enum TipoPagamento {
	DEBITO {
		@Override
		public double calcularDesconto(double valor) {
			return valor * 1.0;
		}
		

	},
	CREDITO {
		@Override
		public double calcularDesconto(double valor) {
			return valor * 0.05;
		}
	}
	
	public abstract calcularDesconto(double valor); //tornamos abstrato por só existe a sobrescrita dele
	
}

```