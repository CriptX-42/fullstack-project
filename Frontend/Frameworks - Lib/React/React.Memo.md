---
Created: 2025-05-08
---
### Definição

É uma **Higher Order Component (HOC)**, usada para memorizar um comportamento funcional - impedir que ela re-renderize se as props não mudarem 

#### Sintaxe

```
const MeuComponente = React.memo((props) =>) {
// logica
}
```

### ✅ Quando usar?

Use `React.memo` quando:

- O componente é **puro** (renderiza o mesmo output dado as mesmas props).
    
- As **re-renderizações desnecessárias** estão impactando a performance.
    
- As props são **simples** e de fácil comparação (ex: strings, numbers, booleanos, arrays/objetos imutáveis).

### Exemplo

```
const Botao = React.memo(({ onClick, label }) => {
  console.log("Renderizou:", label);
  return <button onClick={onClick}>{label}</button>;
});

// Uso
<Botao onClick={() => doSomething()} label="Clique aqui" />

```


> [!Danger] Cuidado
> Objetos, arrays e funções **são comparados por referência**, não por valor. Se você passa uma **função inline** ou um objeto criado no render, o `memo` pode **não evitar** a re-renderização.


