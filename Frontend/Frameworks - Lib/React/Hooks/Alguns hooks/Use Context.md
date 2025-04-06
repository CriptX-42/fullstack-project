---
Created: 2025-05-06
tags:
  - Aprofundar
---
### Conceito
É um recurso do react usado para compartilhar dados e evitar os tais ==prop's Drilling== evitando assim de ficar passando informação de pai pra filho, filho pra pai e tudo mais. Aqui vai um exemplo claro do useContext


### Criação do contexto


```
import { createContext, useContext, useState, ReactNode } from "react";

interface User {
  name: string;
  email: string;
}

interface AuthContextType {
  user: User | null;
  login: (userData: User) => void;
  logout: () => void;
}

const AuthContext = createContext<AuthContextType | undefined>(undefined);

export const AuthProvider = ({ children }: { children: ReactNode }) => {
  const [user, setUser] = useState<User | null>(null);

  const login = (userData: User) => {
    setUser(userData);
  };

  const logout = () => {
    setUser(null);
  };

  return (
    <AuthContext.Provider value={{ user, login, logout }}>
      {children}
    </AuthContext.Provider>
  );
};

export const useAuth = () => {
  const context = useContext(AuthContext);
  if (!context) {
    throw new Error("useAuth must be used within an AuthProvider");
  }
  return context;
};


```


### Envolver no app provider

```
// main.tsx ou App.tsx
import React from "react";
import ReactDOM from "react-dom/client";
import App from "./App";
import { AuthProvider } from "./AuthContext";

ReactDOM.createRoot(document.getElementById("root")!).render(
  <React.StrictMode>
    <AuthProvider>
      <App />
    </AuthProvider>
  </React.StrictMode>
);

```

### Usando o contexto 


```
// App.tsx
import { useAuth } from "./AuthContext";

function App() {
  const { user, login, logout } = useAuth();

  const handleLogin = () => {
    login({ name: "João", email: "joao@example.com" });
  };

  return (
    <div>
      {user ? (
        <>
          <h1>Bem-vindo, {user.name}!</h1>
          <button onClick={logout}>Sair</button>
        </>
      ) : (
        <>
          <h1>Você não está logado.</h1>
          <button onClick={handleLogin}>Entrar</button>
        </>
      )}
    </div>
  );
}

export default App;


```