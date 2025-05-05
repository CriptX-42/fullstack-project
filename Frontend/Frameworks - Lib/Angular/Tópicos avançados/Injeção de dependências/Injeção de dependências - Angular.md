---
Created: 2025-05-05
---
---
É o padrão de design que permite que objetos recebam dependências de fontes externas. Isso facilita, `teste`, `manutenção` e `inversão de controle (IoC)`.

### No angular
- O Angular possui um **injeção de dependência embutida**.
- Usa **decorators como `@Injectable()`** e **injeção via construtor**.

```
@Injectable()
export class ApiService {
  constructor(private http: HttpClient) {}
}

@Component({...})
export class UserComponent {
  constructor(private apiService: ApiService) {}
}

```
