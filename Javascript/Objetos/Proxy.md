- Uma forma de definir comportamento diferente para métodos dentro de um objeto 

````

	let obj = {

        name: "Ricardo",

        age: 27,

      };

  

      let proxy = new Proxy(obj, { <== ==handler (manipulador)==

        get(target, name) {

          return target[name];

        }, // Retorna Ricardo

        set(target, name, value) {

          target[name] = value;

        }, // Pode retornar o valor manipulado depois de compilado e manipular em tempo de execução

      });
````


