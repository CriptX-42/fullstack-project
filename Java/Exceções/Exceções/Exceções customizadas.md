---
Created: 2025-02-02
---
Nosso login customizado:
```
public class CustomLoginException extends Exception{  
    public CustomLoginException() {  
        super("Login inválido");  
    }  
  
    public CustomLoginException(String message) {  
        super(message);  
    }  
}
```

Uso do mesmo:

```
public class TestLogin {  
    public static void main(String[] args) {  
        try {  
            login();  
        } catch (CustomLoginException e) {  
            throw new RuntimeException(e);  
        }  
    }  
  
    private static void login() throws CustomLoginException {  
        String login = "Ricardo";  
        String senha = "123";  
  
        String loginDigitado = "Ricardo";  
        String senhaDigitada = "123546";  
  
        if(!login.equals(loginDigitado) || !senha.equals(senhaDigitada)) {  
            throw new CustomLoginException("Login está errado");  
        }  
  
    }  
}
```

Saída:

```
Exception in thread "main" java.lang.RuntimeException: OException.Exception.CustomLoginException: Login está errado
	at OException.Runtime.TestLogin.main(TestLogin.java:10)
Caused by: OException.Exception.CustomLoginException: Login está errado
	at OException.Runtime.TestLogin.login(TestLogin.java:22)
	at OException.Runtime.TestLogin.main(TestLogin.java:8)

Process finished with exit code 1
```