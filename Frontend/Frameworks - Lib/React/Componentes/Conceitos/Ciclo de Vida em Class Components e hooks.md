---
Created: 2025-03-21
---

> [!NOTE] Para lembrar
> O ciclo de vida de um componente no React pode ser dividido em **três fases**:  
1️⃣ **Montagem (Mounting)** → O componente é criado e inserido no DOM.  
2️⃣ **Atualização (Updating)** → Ocorre quando o `state` ou `props` mudam.  
3️⃣ **Desmontagem (Unmounting)** → O componente é removido do DOM.

```
import React, { Component } from "react";

class ExemploClasse extends Component {
  constructor(props) {
    super(props);
    this.state = { contador: 0 };
    console.log("🔹 Constructor");
  }

  componentDidMount() {
    console.log("✅ Component Did Mount");
  }

  componentDidUpdate() {
    console.log("🔄 Component Did Update");
  }

  componentWillUnmount() {
    console.log("❌ Component Will Unmount");
  }

  incrementar = () => {
    this.setState({ contador: this.state.contador + 1 });
  };

  render() {
    console.log("🎨 Render");
    return (
      <div>
        <p>Contador: {this.state.contador}</p>
        <button onClick={this.incrementar}>Incrementar</button>
      </div>
    );
  }
}

export default ExemploClasse;

```

### Ciclo de vida com hooks (usando useEffect de exemplo)

```
import { useState, useEffect } from "react";

function ExemploHook() {
  const [contador, setContador] = useState(0);

  // Equivalente ao componentDidMount()
  useEffect(() => {
    console.log("✅ Componente Montado");
  }, []);

  // Equivalente ao componentDidUpdate()
  useEffect(() => {
    console.log("🔄 Contador atualizado:", contador);
  }, [contador]);

  // Equivalente ao componentWillUnmount()
  useEffect(() => {
    return () => {
      console.log("❌ Componente será desmontado");
    };
  }, []);

  return (
    <div>
      <p>Contador: {contador}</p>
      <button onClick={() => setContador(contador + 1)}>Incrementar</button>
    </div>
  );
}

export default ExemploHook;

```