---
Created: 2025-01-27
tags:
  - Comandos
  - Docker
---
```
docker run [Container]
```

![[Pasted image 20250127114131.png]]


### Para continuar executando
```
docker run -it ubuntu bash
```

- -it = iteratividade
- bash = terminal

Estou dentro da maquina ubuntu rodando dentro do container docker: 

![[Pasted image 20250127114538.png]]

Ubuntu executando
![[Pasted image 20250127114642.png]]


```
docker run [Container] -P (faz o mapeamento da porta do docker para porta hospedeira)
```

```
docker run [Container] -P (faz o mapeamento da porta do docker para porta hospedeira)
```

```
docker run [Container] -p [porta hospedeira:porta que queremos executar]
```