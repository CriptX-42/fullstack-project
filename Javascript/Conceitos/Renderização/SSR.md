---
Created: 2025-01-23
---
### Server side Rendering
	O processamento é realizado do lado do servidor antes de mandar ao cliente. Toda estrutura de HTML chega completa ao cliente, permitindo que o conteúdo seja exibido ==antes do javascript ser carregado== 

#### Vantagens
- Melhor [[SEO]], já que o HTML renderizado é interpretável pelos motores de busca 
- Tempo de carregamento mais rápido ==First contentful Paint - FCP==, já que HTML é entregue pronto

#### Desvantagem
- Aumenta a carga do lado do servidor
- Experiencia de navegação menos fluida

#### Quando usar?
Recomendadas para blogs, e-commerces ou portais.