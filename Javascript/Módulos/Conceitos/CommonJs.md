---
Created: 2025-06-26
---
---
Basicamente a estrutura de módulos usada principalmente no Node.js para organizar e reutilizar códigosJs. Ele permite exportar e importar funcionalidades entre arquivos.

Exportadora
``` Js
// math.js
function soma(a, b) {
  return a + b;
}

module.exports = {
  soma
};

```

Importadora:
``` Js
// app.js
const math = require('./math');

console.log(math.soma(2, 3)); // 5

```


> [!NOTE] Caracteristicas
> - **Sincrônico**: A importação (`require`) é executada de forma sincrônica. Isso é ideal para ambientes de backend como o Node.js, onde os arquivos já estão no disco.
>- **Escopo de módulo**: Cada arquivo é um módulo com seu próprio escopo.
>- **Cache automático**: Módulos importados com `require` são armazenados em cache na primeira importação.
>- **Usado no Node.js**: É o sistema padrão de módulos em versões mais antigas do Node (antes da introdução oficial dos módulos ES).

|CommonJS (`require`)|ES Modules (`import`)|
|---|---|
|`require()`|`import ... from ...`|
|`module.exports`|`export` / `export default`|
|Sincrônico|Assíncrônico|
|Usado em Node.js (antigo)|Usado no navegador e em Node moderno|
|Não suporta tree-shaking|Suporta tree-shaking|
