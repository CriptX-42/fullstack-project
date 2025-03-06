#### filter(callback)

- Cria um novo array com elementos condicionais que atendem o callback

```
const num = [42, 3, 2];
num.filter(num => {
  if(num === 42) {
    return num
  }
})
Saída: 
[ 42 ]
```