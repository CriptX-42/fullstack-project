---
Created: 2025-05-01
---
----

O `ngStyle` é uma diretiva do Angular usada para **aplicar estilos CSS dinamicamente** a elementos, baseado em expressões do componente.

```
<div [ngStyle]="{ 'color': cor, 'font-size': tamanho + 'px' }">
  Texto estilizado dinamicamente
</div>

```

No componente:
```
cor = 'blue';
tamanho = 18;

```

Resultado no DOM:
```
<div style="color: blue; font-size: 18px;">...</div>

```


### Combinação com `*ngIf`, `*ngFor`, `ngClass`
```
<div *ngIf="item.visivel"
     [ngClass]="{ ativo: item.ativo }"
     [ngStyle]="{ 'opacity': item.ativo ? 1 : 0.5 }">
  {{ item.nome }}
</div>

```
