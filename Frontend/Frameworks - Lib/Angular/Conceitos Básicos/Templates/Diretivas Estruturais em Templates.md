---
Created: 2025-05-02
---
------

Isso nos permite manipular a renderização de elementos:

```
<ng-template #semDados>
  <p>Nenhum dado disponível.</p>
</ng-template>

<div *ngIf="temDados; else semDados">Dados carregados!</div>
```
