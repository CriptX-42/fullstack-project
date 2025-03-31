---
Created: 2025-03-31
---
### Event binding

O _event binding_ conecta eventos DOM (como `click`, `keyup`, `change`) a métodos no TypeScript do componente.

```
<button (click)="onClick()">Clique aqui</button>

```

```
onClick() {
  console.log('Botão clicado!');
}

```

--------

### Template Reference Variables (`#ref`)
O `#ref` cria uma variável de referência no template que pode ser usada dentro do próprio template ou no TypeScript via `@ViewChild`.

```
<input #meuInput type="text">
<button (click)="meuInput.value = ''">Limpar</button>
```

Aqui, `#meuInput` referencia o `<input>`, e podemos manipulá-lo diretamente.

###### Uso no typescript
```
<input #meuInput type="text">
<button (click)="limpar()">Limpar</button>

```

```
import { Component, ViewChild, ElementRef } from '@angular/core';

export class AppComponent {
  @ViewChild('meuInput') meuInput!: ElementRef;

  limpar() {
    this.meuInput.nativeElement.value = '';
  }
}
```

Aqui usamos `@ViewChild` para acessar o elemento no TypeScript.

#### Juntando Event Binding e #ref

```
<input #campoTexto type="text">
<button (click)="mostrarValor(campoTexto.value)">Exibir</button>

```

```
mostrarValor(valor: string) {
  console.log(valor);
}

```
