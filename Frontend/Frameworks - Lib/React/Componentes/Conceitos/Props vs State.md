---
Created: 2025-03-21
---
### Props
São valores passados do componente pai para o componente filho, eles são imutáveis dentro do componente filho, ou seja, o componente filho não pode mudar.

```
function Saudacao({ nome }: { nome: string }) {
  return <p>Olá, {nome}!</p>;
}

function App() {
  return <Saudacao nome="João" />;
}

```

### State

State é o objeto interno de um componente, ele pode ser atualizado se quiser e torna o componente dinâmico e reativo 

```
import { useState } from 'react';

function Contador() {
  const [contador, setContador] = useState(0);

  return (
    <div>
      <p>Contador: {contador}</p>
      <button onClick={() => setContador(contador + 1)}>Incrementar</button>
    </div>
  );
}

```


### Diferenças 
| Característica | Props (`props`) | State (`state`) |
|--------------|---------------|---------------|
| **Quem controla?** | O componente pai | O próprio componente |
| **Mutável?** | ❌ Não | ✅ Sim |
| **Onde é usado?** | Comunicação entre componentes | Gerenciamento interno de dados |
| **Gatilho de re-render?** | Sim | Sim |
| **Pode ser passado para outros componentes?** | ✅ Sim | ✅ Sim (mas precisa ser "elevado") |

### Trabalhando com os dois juntos

```
import { useState } from 'react';

function Contador({ valor }: { valor: number }) {
  return <p>Contador: {valor}</p>;
}

function App() {
  const [contador, setContador] = useState(0);

  return (
    <div>
      <Contador valor={contador} />
      <button onClick={() => setContador(contador + 1)}>Incrementar</button>
    </div>
  );
}

```