---
Created: 2025-04-09
---
----


#### Mege declaration
- Não existe no type

### Keyof
consigo transformar um tipo em outro:

```
type Stringfy<t> = {
	[P in keyof t]: string
}
```


### Outras coisas

- Consigo fazer alias com type
```
// É string é um alias de email
type Email = string

function sendEmail(email: Email) {}