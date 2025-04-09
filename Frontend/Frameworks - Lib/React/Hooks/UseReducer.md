---
Created: 2025-04-09
---
----
### Definição
O `useReducer` é um hook do React que serve como uma alternativa ao `useState` quando você tem uma lógica de atualização de estado mais complexa — ==como múltiplos subvalores ou quando o próximo estado depende do anterior==.

- Anatomia de um useState:
```
const [state,setState] = useState(0)
```

- Anatomia de um useReducer:

```
const [state, dispatch] = useReducer(reducer, initialArg, init);
```

- **`reducer`**: uma função pura que recebe o estado atual e uma ação, e retorna o novo estado.
- **`initialState`**: o estado inicial.
- **`state`**: o estado atual.
- **`dispatch`**: função usada para disparar ações.
- `init` (opcional) o valor da variavel ==(ainda não entendi a aplicação)==


#### Exemplo de uso:

```
import React, { useReducer } from 'react';

const initialState = { count: 0 };

function reducer(state, action) {
  switch (action.type) {
    case 'increment':
      return { count: state.count + 1 };
    case 'decrement':
      return { count: state.count - 1 };
    case 'reset':
      return initialState;
    default:
      throw new Error('Ação desconhecida');
  }
}

export default function Counter() {
  const [state, dispatch] = useReducer(reducer, initialState);

  return (
    <div>
      <p>Contador: {state.count}</p>
      <button onClick={() => dispatch({ type: 'decrement' })}>-</button>
      <button onClick={() => dispatch({ type: 'increment' })}>+</button>
      <button onClick={() => dispatch({ type: 'reset' })}>Resetar</button>
    </div>
  );
}

```


### 🧩 Quando usar `useReducer`?

- Quando o estado tem **várias partes** ou propriedades.
- Quando as atualizações de estado são **condicionais e complexas**.
- Quando quer usar **padrões como Redux** em componentes isolados.


> [!Warning] Uma ideia
> Da para juntar o `useReducer` e `useContext` e fazer um mini `redux`


