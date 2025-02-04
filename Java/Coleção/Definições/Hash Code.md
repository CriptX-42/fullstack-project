---
Created: 2025-02-04
---

> [!NOTE] Definições
> Ele vai trabalhar nas coleções que trabalham com hash


> [!NOTE] Abstração
> Imagine que temos um arrey com 70 milhões dados e precisamos fazer uma busca, fazer essa busca por indice ou "nome" torna algo muito complicado. Por isso temos coleções que usam **hash**. É a melhor forma de identificamos coleções e valores



> [!Warning] Regras de uso
> Se x.equals(y) == true, y.hashCode() == x.hashCode()  
   y.hashCode() == x.hashCode() não necessariamente o equals de y.equals(x) tem que ser true  
   x.equals(y) == false  
   y.hashCode() != x.hashCode() x.equals(y) deverá ser false.
   



Exemplo de uso: 
```
public class Smartphone {  
    private String serialNumber;  
    private String marca;  
  
    public Smartphone(String serialNumber, String marca) {  
        this.serialNumber = serialNumber;  
        this.marca = marca;  
    }  
  
    @Override  
    public boolean equals(Object obj) {  
        if(obj == null) return false;  
        if(this == obj) return true;  
        if(this.getClass() != obj.getClass()) return  false;  
        Smartphone smartphone = (Smartphone) obj;  
        return serialNumber != null && serialNumber.equals(smartphone.serialNumber);  
    }  
  
	@Override  
    public int hashCode() {  
        return serialNumber == null ? null :  this.serialNumber.hashCode();  
    }  
  ...  
}
```



> [!Warning] Outras regras
> Quanto mais especifico for o hash para cada um dos objetos, melhor
> Quando tivermos implementando hash code ele deve dar match no equals, **se tivermos um atributo no hash devemos ter uma comparação dele no equals** para mantermos uma consistência 
