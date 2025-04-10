---
Created: 2025-04-10
---
-----

### Definição
- Um simples hook que retorna um objeto com uma propriedade `.current`, essa referencia é `persistente entre renderizações`.

🔹 Exemplo básico – Guardar um valor mutável

```
import { useRef } from 'react';

function TimerComponent() {
  const count = useRef(0);

  const handleClick = () => {
    count.current += 1;
    console.log('Count:', count.current);
  };

  return (
    <button onClick={handleClick}>
      Clique para incrementar (veja no console)
    </button>
  );
}

```

![[Gravação de tela de 2025-04-10 19-29-56.webm]]
==Aqui, o `count.current` vai manter seu valor entre cliques, mas **não vai causar um re-render** quando mudar.==

🔹 Exemplo clássico – Acessar um elemento DOM

```
import { useRef, useEffect } from 'react';

function InputFocus() {
  const inputRef = useRef(null);

  useEffect(() => {
    // Foca no input quando o componente monta
    inputRef.current.focus();
  }, []);

  return <input ref={inputRef} placeholder="Digite aqui..." />;
}

```
Esse é um dos usos mais comuns: controlar o foco de inputs, rolagem, etc.

### 🔹 Dica de ouro: Quando usar?

- Quando você precisa **manter um valor entre renders**, mas não quer re-renderizar o componente.
- Para **armazenar referências de DOM** (`ref` em inputs, divs, etc).
- Para **guardar valores anteriores** (ex: valor anterior de uma prop/state).

|Tipo de variável|Valor persiste entre renders?|Causa re-render?|
|---|---|---|
|`let`, `const`|❌ Não|❌ Não|
|`useRef`|✅ Sim|❌ Não|
|`useState`|✅ Sim|✅ Sim|