---
Created: 2025-05-02
---
-----

O ciclo de vida no angular é um método que permite a execução de alguns códigos.

Vamos aqui a alguns ciclos:


#### ngOnChanges

==Uso médio==
- É chamada sempre que uma propriedade de entrada munda no componente
- O `SimpleChanges` como argumento contem as informações que mudaram

```
ngOnChanges(changes: SimpleChanges): void {
  console.log(changes);
}
```

#### ngOnInit

==Uso Grande==
- É Chamado uma vez apos iniciar o componente

```
ngOnInit(): void {
  console.log('Componente inicializado');
}

```

#### ngDoCheck (nunca usei isso)
- É chamado sempre que o angular verifica uma mudança
- É bom pra implementar lógica de verificação de mudança personalizada

```
ngDoCheck(): void {
  console.log('Verificação personalizada de mudanças');
}

```


#### ngAfterContentInit
- Chamado logo após o angular projetar um conteúdo externo (com ng-content)

```
ngAfterContentInit(): void {
  console.log('Conteúdo projetado');
}

```


#### ngAfterContentChecked

- Após o angular verificar o conteúdo projetado

```
ngAfterContentChecked(): void {
  console.log('Conteúdo projetado verificado');
}

```

### ngAfterViewInit

==Uso baixo==
- Chamado uma vez após iniciar a visualização dos componentes e dos filhos (se tiver)

```
ngAfterViewInit(): void {
  console.log('Visualização do componente inicializada');
}

```

### ngAfterViewChecked

- Chamado só quando o angular renderiza os componentes filhos

```
ngAfterViewChecked(): void {
  console.log('Visualização do componente verificada');
}

```

### ngOnDestroy

==Uso bastante==
- Chamado quando componente é destruido
- Bom para limpar coisas e cancelar subscrição

```
ngOnDestroy(): void {
  console.log('Componente destruído');
}
```