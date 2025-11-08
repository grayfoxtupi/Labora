# 🧱 Labora – Documento de Arquitetura

## 1. Introdução

Este documento descreve a **arquitetura do sistema Labora**, um aplicativo multiplataforma que conecta **profissionais autônomos** e **clientes** em busca de serviços locais.  
O projeto utiliza **Kotlin Multiplatform** para o aplicativo e **Spring Boot** para o backend, garantindo escalabilidade, segurança e manutenibilidade.

---

## 2. Arquitetura Geral

O **Labora** adota uma **arquitetura em camadas**, separando responsabilidades entre o frontend, backend e infraestrutura.  

### 🔸 Camada 1 – Frontend (Kotlin Multiplatform)
Responsável pela interface do usuário e experiência visual, desenvolvida com **Compose Multiplatform**, compartilhando lógica entre Android e iOS.

**Subcamadas:**
- **UI Layer:** Telas e componentes visuais (Compose)
- **ViewModel Layer:** Lógica de apresentação e controle de estado (Kotlin Flow)
- **Data Layer:** Acesso a APIs (Ktor Client) e persistência local (SQLDelight)

### 🔸 Camada 2 – Backend (Spring Boot)
Responsável pela lógica de negócio, autenticação, persistência e comunicação com o banco de dados.

**Módulos principais:**
- **API Layer (Controller):** Exposição de endpoints REST
- **Service Layer:** Processamento de regras de negócio
- **Repository Layer:** Comunicação com o banco de dados (Spring Data)
- **Database Layer:** PostgreSQL ou MongoDB

### 🔸 Camada 3 – Infraestrutura
- **Hospedagem:** DigitalOcean (Docker + Nginx + HTTPS)
- **Banco de Dados:** PostgreSQL (relacional) ou MongoDB (documental)
- **Mensageria (futuro):** RabbitMQ ou Kafka (para notificações e eventos)
- **Storage (futuro):** AWS S3 ou DigitalOcean Spaces (para imagens de perfil)

---

## 3. Padrões de Arquitetura

| Camada | Padrão | Descrição |
|---------|---------|-----------|
| App (Kotlin) | **MVVM (Model–View–ViewModel)** | Organização modular entre UI, lógica e dados |
| Backend | **Hexagonal / Clean Architecture** | Facilita testes e integração com múltiplos serviços |
| API | **RESTful** | Estrutura simples e padronizada |
| Comunicação | **DTOs + JSON** | Transferência de dados leve e independente |
| Autenticação | **JWT + Spring Security** | Proteção baseada em tokens seguros |

---

## 4. Fluxo de Dados

```plaintext
Usuário (App)
   ↓
Interface (Compose)
   ↓
ViewModel (KMP)
   ↓
Ktor Client → API REST (Spring Boot)
   ↓
Controller → Service → Repository → Banco de Dados
