# 🗃️ Modelo de Dados – Labora

Este documento descreve as principais entidades do sistema **Labora**, seus atributos, relacionamentos e exemplos de representação.  
O modelo foi projetado para ser compatível tanto com **PostgreSQL** quanto com **MongoDB**.

---

## 🧑 Entidade: User

Representa o usuário do sistema (cliente ou profissional).

| Campo | Tipo | Descrição |
|--------|------|------------|
| `id` | UUID / ObjectId | Identificador único do usuário |
| `name` | String | Nome completo do usuário |
| `email` | String | E-mail de login e contato |
| `passwordHash` | String | Senha criptografada |
| `role` | Enum (`CLIENT`, `PROFESSIONAL`) | Define o tipo de usuário |
| `phone` | String | Número de telefone |
| `createdAt` | DateTime | Data de criação do registro |
| `updatedAt` | DateTime | Data da última atualização |

### Exemplo (JSON)
```json
{
  "id": "f82a71d2-891a-4e2c-9054-41c9b23b10ab",
  "name": "Maria Souza",
  "email": "maria@example.com",
  "role": "PROFESSIONAL",
  "phone": "+55 11 98888-7777",
  "createdAt": "2025-11-06T18:00:00Z"
}
