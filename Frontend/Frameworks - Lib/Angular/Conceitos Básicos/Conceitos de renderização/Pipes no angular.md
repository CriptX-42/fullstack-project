---
Created: 2025-05-02
---
-----
Uma forma sutil de alterarmos a forma como um valor está sendo apresentada na view e não afetarmos o valor original.

```
import { Pipe, PipeTransform } from '@angular/core';

@Pipe({ name: 'inverter' })
export class InverterPipe implements PipeTransform {
  transform(valor: string): string {
    return valor.split('').reverse().join('');
  }
}

```

```
<p>{{ 'Angular' | inverter }}</p>
<!-- Saída: ralugnA -->

```


> [!Warning] Performance
> - Pipes **puros (pure pipes)** são recalculados apenas quando os inputs mudam.
> - Pipes **impuros (impure pipes)** são recalculados a cada detecção de mudança (podem impactar performance).
