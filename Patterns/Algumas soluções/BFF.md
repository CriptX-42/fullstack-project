---
Created: 2025-02-03
---
---
Backend for Frontend

Um padrão de arquitetura que você cria um backend especifico para um frontend. (por exemplo, para um app web, outro para mobile, etc).

Em vez de criar um bk generico, que atende todos os tipos de cliente. Você cria um backend personalizado para cada tipo de cliente, com suas regras, chamadas e melhor forma para o backend funcionar.

### 🧱 Benefícios do BFF

- 🔒 **Segurança**: o frontend não precisa se conectar diretamente a todos os serviços.
- ⚙️ **Desempenho**: o BFF pode otimizar as requisições (ex: cache, batch requests).
- 📱 **Personalização**: cada frontend recebe os dados do jeito que precisa.
- 💼 **Separação de responsabilidades**: o frontend se preocupa só com UI, o BFF lida com regras de negócio específicas da interface.