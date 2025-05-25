---
Created: 2025-05-25
---
---


> [!Warning] Um adendo as versões
> Fiz esse tutorial baseado no angular 17. 

### 1. Passo, criar o host (shell)

- Ao criar um host nós temos uma aplicação "pai", onde terá todos os MFE's necessários para execução do nosso projeto.
- Algumas características. Ele não necessariamente precisa ter um framework de front nele, mas precisa ter o tal do ==webpack.config== para o gerenciamento dos nossos MFE's

### 2. Criar o MFE em sí
- Esse passo nós estamos dando entrada no nosso micro, ele sim precisa ter uma lib/framework de front embarcado, e também precisa ter o ==webpack==

### 3. Module Federation

- Instalar o [[Module Federation]] em ambos os projetos para que possamos expor e importar os módulos necessários para fazer acontecer.

---
### 4 . Vamos as configurações

### 4.1 - configurando mfe

- Vamos primeiro importar algumas coisas no nosso módulo, assim:

```typescript
@NgModule({
declarations: [ProfileComponent],
imports: [
	CommonModule,
	BrowserModule,
	RouterModule.forChild([{ path: '', component: ProfileComponent }]),
],
})

export class ProfileModule {}
```

Nas rotas:
``` typescript
const routes: Routes = [{ path: 'profile', component: ProfileComponent }];

@NgModule({
imports: [RouterModule.forRoot(routes)],
exports: [RouterModule],
})

export class AppRoutingModule {}
```

No app module:
``` typescript
@NgModule({
declarations: [AppComponent],
imports: [BrowserModule, AppRoutingModule, ProfileModule],
providers: [],
bootstrap: [AppComponent],
})
```

**Agora vamos expor tudo isso no nosso webpack.config.js**:
``` javascript
module.exports = {
  output: {
    uniqueName: "mfe1",
    publicPath: "auto",
    scriptType: "text/javascript",
  },
  optimization: {
    runtimeChunk: false,
  },
  resolve: {
    alias: {
      ...sharedMappings.getAliases(),
    },
  },
  experiments: {
    outputModule: true,
  },
  plugins: [
    new ModuleFederationPlugin({
      // For remotes (please adjust)
      name: "mfe1",
      filename: "remoteEntry.js",
      exposes: {
        "./ProfileModule": "./src/app/profile/profile.module.ts", // nosso perfil importado
      },
};
```
- Quando instamos o module federation, configuramos nosso mfe para subir na porta *localhost:4201*, podemos escolher qualquer porta, mas configurei essa.

> [!Danger] Um adendo
> Sempre adicionar `scriptType: "text/javascript",` imagino que isso sirva para facilitar a interpretação dos módulos expostos
> Cuidado com os componentes standalone: Como não usam o NgModule, então fica mais complicado de se trabalhar (em teoria)


#### 4.2 Configurando o host

Vamos começar com o webpack:
``` typescript
module.exports = {
  output: {
    uniqueName: "hostApp",
    publicPath: "auto",
    scriptType: "text/javascript",
  },
  optimization: {
    runtimeChunk: false,
  },
  resolve: {
    alias: {
      ...sharedMappings.getAliases(),
    },
  },
  experiments: {
    outputModule: true,
  },
  plugins: [
    new ModuleFederationPlugin({

      // For hosts (please adjust)
      remotes: {
        mfe1: "http://localhost:4201/remoteEntry.js", //importando nosso mfe
      },
  ],
};
```

Agora vamos usar o mfe. No app routes:
``` typescript
export const routes: Routes = [
  {
    path: 'remote',
    loadChildren: () => //Funiona tanto para o standalone quanto NgModule
      loadRemoteModule({ // uma propriedade do federation
        remoteEntry: 'http://localhost:4201/remoteEntry.js',
        remoteName: 'mfe1',
        exposedModule: './ProfileModule',
      }).then((m) => m.ProfileModule),
  },
];
```

E pronto, nosso mfe está usável.

