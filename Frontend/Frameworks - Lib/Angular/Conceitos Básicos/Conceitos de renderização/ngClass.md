---
Created: 2025-05-02
---
----
Uma forma de manipularmos classes dinamicamente

```
<div [ngClass]="'minha-classe'"></div>

```



### Temos outra forma de usar

Com String
```
<div [ngClass]="'classe-a classe-b'"></div>

```

Com Array
```
<div [ngClass]="['classe-a', 'classe-b']"></div>

```

Com objetos
```
<div [ngClass]="{ 'ativo': isAtivo, 'erro': hasErro }"></div>

```


----
Na pratica:

```
export class MeuComponente {
  isAtivo = true;
  hasErro = false;
}

```

```
<p [ngClass]="{ 'verde': isAtivo, 'vermelho': hasErro }">
  Status
</p>

```

```
.verde {
  color: green;
}
.vermelho {
  color: red;
}

```


> [!Danger] Cuidado
> Nunca usamos com interpolação pois ngClass é um propertyBinding 


- Com NgFor
```
<div *ngFor="let item of lista" [ngClass]="{ 'selecionado': item.id === selecionadoId }">
  {{ item.nome }}
</div>

```