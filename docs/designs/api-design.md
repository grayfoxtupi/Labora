# 📡 API Design — Labora

## 🧩 Visão Geral

A API do **Labora** será responsável por fornecer todos os recursos necessários para o funcionamento do aplicativo, incluindo:
- Cadastro e autenticação de usuários (profissionais e clientes)
- Listagem e filtragem de profissionais
- Criação e gerenciamento de solicitações de serviço
- Sistema de mensagens entre cliente e profissional
- Avaliações e feedbacks
- Integração futura com meios de pagamento

A API será construída com **Spring Boot**, seguindo o padrão **RESTful** e retornando dados no formato **JSON**.

---

## 🔒 Autenticação e Segurança

- **Protocolo:** HTTPS obrigatório  
- **Método:** JWT (JSON Web Token)  
- **Fluxo:**
  1. O usuário realiza login (`/auth/login`)
  2. Recebe um token JWT
  3. O token é enviado no cabeçalho `Authorization: Bearer <token>` em todas as requisições autenticadas

**Exemplo de Cabeçalho:**
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...

---

## 🧠 Padrões Gerais

| Item | Padrão |
|------|--------|
| **Formato de resposta** | JSON |
| **Paginação** | `?page=1&size=20` |
| **Ordenação** | `?sort=field,asc` |
| **Erros** | HTTP Status Codes + mensagem padrão |
| **Versionamento** | `/api/v1/...` |

**Exemplo de resposta padrão e de erro:**
```json
{
  "success": true,
  "data": {},
  "message": "Operação realizada com sucesso"
}

{
  "success": false,
  "error": "User not found",
  "code": 404
}
