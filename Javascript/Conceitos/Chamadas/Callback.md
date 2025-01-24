- Por definição, é uma função que é passada como argumento em outra função e será executada dentro dessa "função parâmetro", normalmente em resposta a um evento ou ao termino de uma operação assíncrona 

Exemplo básico:
```
function saudacao(nome, callback) {
  console.log(`Olá, ${nome}`)
  callback();
}

function pergunta() {
  console.log("Tudo bem?")
}

saudacao("Ricardo", pergunta)


Saída: 
Olá, Ricardo
Tudo bem?
```

##### Outros usos assíncronos

Callback é bastante usado em conjunto com [[setTimeout]] pois faz parte de sua estrutura.

##### Problemas do callback

	Existe um problema de estrutura chamado ==callback hell== basicamente é quando você precisa fazer uma sequencia de operações assíncronas, e cada operação dependente do resultado anterior, resultando num código com muitos niveis de indentação. Até quebrando o [[SOLID]]
	A melhor solução para resolver o callback hell é você modularizar bem o código.

Exemplo de callback Hell

````
setTimeout(() => {
    console.log('Primeiro passo');
    setTimeout(() => {
        console.log('Segundo passo');
        setTimeout(() => {
            console.log('Terceiro passo');
            setTimeout(() => {
                console.log('Quarto passo');
            }, 1000);
        }, 1000);
    }, 1000);
}, 1000);

````
