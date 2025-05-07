---
Created: 2025-05-06
tags:
  - Dicionário
---
---



> [!NOTE] Warning
> - Sempre use `fixture.detectChanges()` após mudar algo no componente ou simular uma ação.
>- Você pode usar `fixture.debugElement` para buscas mais precisas com `By.css()`:
```typescript
const alert = fixture.debugElement.query(By.css('.alert')).nativeElement;

```
#### Testando um serviço (exemplo)
[[Teste de serviço (angular)]]

#### Testando Component Bindings
[[Testando Component Bindings]]

