---
Created: 2025-05-02
---
------
Basicamente é a forma mais simples do angular lidar dinamicamente com valores do componente a serem renderizados no DOM ou de componentes pai/filho.

```
<img [src]="imagemUrl" />
```

**Diferença entre Interpolação e Property Binding**

```
<img src="{{ imagemUrl }}" />     <!-- Interpolação -->
<img [src]="imagemUrl" />         <!-- Property Binding -->
```


> [!NOTE] Diferenças
> A interpolação trata os valores como string
> A interpolação trata os valores como algo real no DOM, é mais seguros para coisas não booleanas e não-string


- Outros exemplos:

```
<!-- Desativa um botão -->
<button [disabled]="isDesativado">Salvar</button>

<!-- Define a largura dinamicamente -->
<div [style.width.px]="largura"></div>

```

-----


Componente filho:

```
// filho.component.ts
@Input() titulo: string;

```

