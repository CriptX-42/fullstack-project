---
Created: 2025-04-27
---
-----
### Vamos conhecer mais sobre a estrutura


🔹 1. **Modules (Módulos)**
	- Organizadores de funcionalidades
	- Um app angular tem 1 ou mais módulos (`@NgModule`)
	- `AppModule`, `SharedModule`, `FeatureModule` são bons exemplos disso

🔹 2. **Components (Componentes)**
	- A menor unidade visual da aplicação.
	- Composto por um **template** (HTML), **classe** (TypeScript) e **estilo** (CSS/SCSS).
	- Botões, cards e paginas são um bom exemplo disso

🔹 3. **Templates + Directives + Pipes**
	- **Templates**: Definem o que será renderizado
	- **Directives**: Comportamentos adicionais nos elementos (`ngIf`, `ngFor` ...)
	- `Pipes`: Transformações de dados nos Templates `date`, `currency`, pipes customizados).

🔹 4. **Services (Serviços) e Dependency Injection (DI)**
	- Serviços são usados para compartilhar dados, lógica e comunicação entre componentes.
	- Angular usa **injeção de dependência** para criar e fornecer instâncias dos serviços.

🔹 5. **Routing (Roteamento)**
	- Gerencia a navegação entre componentes/paginas e afins.
	- Definido através do `RouterModule`
	- Usa conceitos como `Routes`, `Lazy Loading`, `Guards` e `Resolvers`.

🔹 6. **State Management (Gerenciamento de Estado)** _(opcional, mas comum)_
	- @ngrx/store
	- NgRx Component Store
	- Akita
	- Ou até serviços próprios com `BehaviorSubject`.

🔹 7. **HTTP Client**
	- Comunicação com APIs através do `HttpClientModule`.
	- Permite fazer requisições, interceptar chamadas (com **interceptors**), e tratar erros.

🔹 8. **Arquitetura Avançada** _(apps mais complexos)_
	- **Camadas** bem definidas:
		- **Core**: Serviços globais, guards, interceptors.
		- **Shared**: Componentes, pipes, e diretivas reutilizáveis.
		- **Feature Modules**: Cada feature isolada (Ex: módulo de Usuários, módulo de Produtos).
		- **Facade Pattern**: Serviços intermediários para reduzir dependência entre camadas.

![[Pasted image 20250427191501.png]]




> [!Warning] Alguns adendos sobre verões
> O angular 19 pode trazer muitas melhorias, uma delas é o componente `Standalone`, onde não precisa do `NgModule`. Mas a ideia da estrutura é a mesma 

