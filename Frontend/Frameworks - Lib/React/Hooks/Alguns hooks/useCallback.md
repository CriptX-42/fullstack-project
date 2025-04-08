---
Created: 2025-04-08
tags:
  - Aprofundar
---
### Definição
É usado para **memorizar uma função**, evitando recriações desnecessarias  — especialmente útil quando você passa essas funções como props para componentes filhos otimizados com `React.memo`.

### Sintaze base

```
const memoizedCallback = useCallback(
  () => {
    // função que será memorizada
  },
  [dependências], // array de dependências
);

```

### Quando usar

É preciso ter um pouco de cautela ao usar o useCallback, na verdade até hoje não achei muito sentido em usar nos componentes pequenos

```
import React, { useState, useCallback } from 'react';

// Componente filho
const Button = React.memo(({ onClick }: { onClick: () => void }) => {
  console.log('Renderizou <Button />');
  return <button onClick={onClick}>Clique aqui</button>;
});

// Componente pai
export default function App() {
  const [count, setCount] = useState(0);

  // Essa função só vai ser recriada se 'count' mudar
  const handleClick = useCallback(() => {
    console.log('Botão clicado');
  }, []);

  return (
    <div>
      <h1>Contador: {count}</h1>
      <button onClick={() => setCount(count + 1)}>Incrementar contador</button>
      <Button onClick={handleClick} />
    </div>
  );
}

```

 **O que esse exemplo mostra:**

- Sem `useCallback`, toda vez que o `App` renderiza, a função `handleClick` seria recriada.
    
- Como o `Button` é um `React.memo`, ele **só re-renderiza se as props mudarem**.
    
- `useCallback` garante que a **mesma instância da função** seja passada como prop — evitando re-renderizações desnecessárias do filho.