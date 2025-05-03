---
Created: 2025-05-03
---
---
![[Pasted image 20250503155856.png]]


### Sobre
É uma forma elegante do angular de interceptar requisiçẽos e respostas HTTP. Ele é muito usado para:

- Adicionar headers (como tokens de autenticação),

- Logar requisições/respostas,

- Tratar erros globais (como redirecionar para login em caso de 401),

- Mostrar ou esconder spinners de carregamento.

Basicamente é o `HttpInterceptor` intercepta tudo no `HTTPClient`


### Exemplo interceptando token JWT

```
import { Injectable } from '@angular/core';
import { HttpInterceptor, HttpRequest, HttpHandler, HttpEvent } from '@angular/common/http';
import { Observable } from 'rxjs';

@Injectable()
export class AuthInterceptor implements HttpInterceptor {

  intercept(req: HttpRequest<any>, next: HttpHandler): Observable<HttpEvent<any>> {
    const token = localStorage.getItem('token');

    if (token) {
      const cloned = req.clone({
        headers: req.headers.set('Authorization', `Bearer ${token}`)
      });
      return next.handle(cloned);
    }

    return next.handle(req);
  }
}

```


### Registrando um interceptor 
Geralmente é registrado nos `providers` do `AppModule`.

```
import { HTTP_INTERCEPTORS } from '@angular/common/http';
import { AuthInterceptor } from './auth.interceptor';

@NgModule({
  // ...
  providers: [
    {
      provide: HTTP_INTERCEPTORS,
      useClass: AuthInterceptor,
      multi: true
    }
  ]
})
export class AppModule { }

```

O `multi: true` é essencial para que o Angular saiba que você pode ter vários interceptors registrados ao mesmo tempo.

