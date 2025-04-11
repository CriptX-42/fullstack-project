---
Created: 2025-04-11
---
---------



> [!Warning] Angular não tem DOM virtual
> Exatamente, ele usa o DOM real, ele faz uma compilação dos Templates e injeta no dom real



### Change Detection concept
Angular detecta mudanças por meio de um ciclo chamado **Change detection**, onde ele verifica todos os bindings e atualiza o DOM quando necessario.

## Comparação com react

| Conceito                 | React                              | Angular                                        |
| ------------------------ | ---------------------------------- | ---------------------------------------------- |
| **DOM**                  | Virtual DOM                        | DOM real                                       |
| **Montagem**             | Reconciliação + atualização diffs  | Compilação de template + bindings              |
| **Detecção de mudanças** | Manual (via estado/props)          | Automática com Change Detection                |
| **Hooks/Ciclo de Vida**  | `useEffect`, `useLayoutEffect`     | `ngOnInit`, `ngAfterViewInit`                  |
| **Controle do DOM**      | Declarativo (via JSX)              | Declarativo (via templates)                    |
| **Performance**          | Otimizado por diffs no Virtual DOM | Otimizado por zone.js e estratégia de detecção |
