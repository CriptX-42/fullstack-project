---
Created: 2025-05-03
---
-----
São basicamente implementações usadas para proteger uma rota. Validando uma condição mesmo antes de continuar com a navegação do usuário.

Temos 4 tipos de ação:
1. CanActivate (muito usado)
2. CanLoad
3. CanDectivate
4. Resolve

----
### Implementação

#### CanActivate
	É usado para determinar se uma rota pode ser acessada. Pode ser muito util com autenticação por exemplo

```
import { Injectable } from '@angular/core';
import { CanActivate, ActivatedRouteSnapshot, RouterStateSnapshot, Router } from '@angular/router';
import { Observable } from 'rxjs';
import { AuthService } from './auth.service';

@Injectable({
  providedIn: 'root'
})
export class AuthGuard implements CanActivate {

  constructor(private authService: AuthService, private router: Router) {}

  canActivate(
    next: ActivatedRouteSnapshot,
    state: RouterStateSnapshot): Observable<boolean> | Promise<boolean> | boolean {
      if (this.authService.isAuthenticated()) {
        return true;
      } else {
        this.router.navigate(['/login']);
        return false;
      }
  }
}

```

#### CanLoad
impede o carregamento de módulos preguiçosos ==(lazy-loaded modules)== até que uma condução seja atendida. Serve para impedir que módulos sejam carregados sem autorização 
```
@Injectable({
  providedIn: 'root'
})
export class AuthGuard implements CanLoad {

  constructor(private authService: AuthService, private router: Router) {}

  canLoad(): Observable<boolean> | Promise<boolean> | boolean {
    if (this.authService.isAuthenticated()) {
      return true;
    } else {
      this.router.navigate(['/login']);
      return false;
    }
  }
}

```


> [!Warning] Um pouco detalhado
> **Funcionamento:**  
> Evita até mesmo o **download do módulo lazy**, o que é mais eficiente em termos de segurança e performance.


#### CanDeactivate 
Muito usado para impedir que o usuário saia de uma rota. Como para impedir que ele saia sem salvar algo por exemplo.

```
@Injectable({
  providedIn: 'root'
})
export class UnsavedChangesGuard implements CanDeactivate<CanComponentDeactivate> {

  canDeactivate(component: CanComponentDeactivate): Observable<boolean> | Promise<boolean> | boolean {
    return component.canDeactivate ? component.canDeactivate() : true;
  }
}

export interface CanComponentDeactivate {
  canDeactivate: () => Observable<boolean> | Promise<boolean> | boolean;
}

```

#### Resolve
Usado para pré-carregamento. Ele permite que os dados sejam carregados antes que o componente seja exibido

```
@Injectable({
  providedIn: 'root'
})
export class DataResolver implements Resolve<any> {

  constructor(private dataService: DataService) {}

  resolve(route: ActivatedRouteSnapshot, state: RouterStateSnapshot): Observable<any> {
    return this.dataService.getData();
  }
}

```

-----
### Aplicando o guards
```
const routes: Routes = [
  { path: 'protected', component: ProtectedComponent, canActivate: [AuthGuard] }
];

```