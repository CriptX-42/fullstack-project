- Uma forma mais simples de escrever sem a necessidade de then e catch


> **Async**
> 	Torna a função assíncrona,  retorna promise e dentro do async, você usa o ==await==
> **Await** 
> 	Aguarda a promise e retorna o valor.
> 	Se for rejeitada o código ==pause== aparece, até que a promise seja resolvida. Sem bloquear o código

````
const fetchData = () => {
    return new Promise((resolve, reject) => {
      setTimeout(() => {
        const success = true;
        
        if (success) resolve("Dados carregados!");
        else reject("Erro ao carregar os dados!");

      }, 1000);
    });
  };

  
  

const loadData = async () => {
  try {
    const data = await fetchData();
    console.log(data); // "Dados carregados!"
  } catch (error) {
    console.error(error); // "Erro ao carregar os dados!"
  }
};

loadData();
```