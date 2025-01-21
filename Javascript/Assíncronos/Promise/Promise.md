- Um objeto que representa a conclusão ou falha de uma operação assíncrona, podendo ter como status: 

| Pending  | Fulled    | Rejected  |
| -------- | --------- | --------- |
| Pendente | Concluida | Rejeitada |
Para lidar com os resultados é comum usar o then e catch 

```
const fetchData = new Promise((resolve, reject) => {
  setTimeout(() => {
    const testeDeErro = true
    if(testeDeErro) {
       return resolve("carregando dados")
    }
    if(!testeDeErro) {
      return reject("erro ao carregar dados")
    }
  },1000)
})

fetchData.then((data) => {console.log(data)})
.catch(error => console.log(error))
```

