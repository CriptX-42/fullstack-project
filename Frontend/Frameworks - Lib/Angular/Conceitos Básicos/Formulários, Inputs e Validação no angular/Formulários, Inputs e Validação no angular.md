---
Created: 2025-05-02
---
----
### Vamos a pratica
Quando trabalhamos com forms no angular, estamos lidando com dois tipo de módulos. Ou `ReactiveFormsModule` ou `FormsModule`, depende muito da abordagem para criar os:

- As abordagens
> [!NOTE] Template-driven (FormsModule)
> - Utiliza diretivas no HTML
> - Simples 
> - Ideial para formulários simples


> [!NOTE] Reactive Forms (ReactiveFormsModule)
> - Totalmente baseado no TS
> - Flexivel e escalável
> - Ideal para forms complexos e dinamicos


------

Configuração básica:

```
// app.module.ts
import { FormsModule, ReactiveFormsModule } from '@angular/forms';

@NgModule({
  imports: [FormsModule, ReactiveFormsModule],
})
export class AppModule {}

```

- Componente

```
import { Component, OnInit } from '@angular/core';
import { FormBuilder, FormGroup, Validators } from '@angular/forms';

@Component({
  selector: 'app-user-form',
  templateUrl: './user-form.component.html',
})
export class UserFormComponent implements OnInit {
  form!: FormGroup;

  constructor(private fb: FormBuilder) {}

  ngOnInit() {
    this.form = this.fb.group({
      name: ['', [Validators.required, Validators.minLength(3)]],
      email: ['', [Validators.required, Validators.email]],
      age: [null, [Validators.min(18)]],
    });
  }

  submit() {
    if (this.form.valid) {
      console.log(this.form.value);
    } else {
      this.form.markAllAsTouched();
    }
  }
}

```

- Html

```
<form [formGroup]="form" (ngSubmit)="submit()">
  <label>
    Nome:
    <input formControlName="name" />
    <span *ngIf="form.get('name')?.invalid && form.get('name')?.touched">
      Nome é obrigatório (mín. 3 caracteres).
    </span>
  </label>

  <label>
    Email:
    <input formControlName="email" />
    <span *ngIf="form.get('email')?.invalid && form.get('email')?.touched">
      Email inválido.
    </span>
  </label>

  <label>
    Idade:
    <input type="number" formControlName="age" />
    <span *ngIf="form.get('age')?.hasError('min')">
      Idade mínima é 18.
    </span>
  </label>

  <button type="submit">Enviar</button>
</form>
```

