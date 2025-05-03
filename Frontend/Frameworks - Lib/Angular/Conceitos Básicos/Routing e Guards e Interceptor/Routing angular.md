---
Created: 2025-05-02
---
------
O Routing é responsavel pelo gerenciamento das paginas dentro da aplicação, ela permite a navegação entre diferentes componentes, permitindo uma experiencia de SPA.

### Como funciona isso
Definindo rotas:
O Angular usa um módulo de roteamento, normalmente definido no `AppRoutingModule`.

```
import { NgModule } from '@angular/core';
import { RouterModule, Routes } from '@angular/router';
import { HomeComponent } from './home/home.component';
import { AboutComponent } from './about/about.component';

const routes: Routes = [
  { path: '', component: HomeComponent },
  { path: 'about', component: AboutComponent }
];

@NgModule({
  imports: [RouterModule.forRoot(routes)],
  exports: [RouterModule]
})
export class AppRoutingModule { }

```

#### Usando a navegação
- No HTML
```
<a routerLink="/about">About</a>

```

- No Typescript
```
import { Router } from '@angular/router';

constructor(private router: Router) {}

navigateToAbout() {
  this.router.navigate(['/about']);
}

```


> [!NOTE] Exibindo o componente
> O Componente correspondente a uma rota será renderizado na diretiva `<router-outlet></router-outlet>`, ele mostra o componente ativo de acordo com a rota
> 

