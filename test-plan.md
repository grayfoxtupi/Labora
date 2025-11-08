# 🧪 Plano de Testes – Labora

Este documento define a estratégia, o escopo e o cronograma de testes do projeto **Labora**, garantindo a qualidade e confiabilidade do aplicativo antes e após o lançamento.

---

## 🎯 1. Objetivo

O objetivo deste plano é assegurar que todas as funcionalidades do **Labora** — tanto no aplicativo (Kotlin Multiplatform) quanto no backend (Spring Boot) — funcionem corretamente, sejam seguras e entreguem uma boa experiência ao usuário.

---

## 🧩 2. Escopo dos Testes

Os testes abrangerão todas as camadas do sistema:

- **Frontend (App Mobile):** fluxos de cadastro, login, chat, busca, agendamento e avaliação.  
- **Backend (API REST):** autenticação, requisições HTTP, regras de negócio e persistência.  
- **Banco de Dados:** integridade e consistência dos dados (PostgreSQL/MongoDB).  
- **Integrações Futuras:** pagamentos, notificações e serviços externos (ex.: Google Maps).

---

## 🧠 3. Estratégia de Testes

| Tipo de Teste | Descrição | Ferramentas |
|----------------|------------|-------------|
| **Teste Unitário** | Valida funções e componentes isolados. | JUnit (Kotlin), Mockito, Kotest |
| **Teste de Integração** | Verifica a comunicação entre módulos (ex.: API ↔ DB). | Spring Test, Testcontainers |
| **Teste de API** | Garante que os endpoints REST retornem as respostas esperadas. | Postman, REST Assured |
| **Teste de UI** | Avalia a interação do usuário e fluxo de telas. | Espresso (Android), KMP UI Test |
| **Teste de Performance** | Mede tempos de resposta e estabilidade. | JMeter, k6 |
| **Teste de Segurança** | Avalia autenticação, criptografia e vulnerabilidades. | OWASP ZAP, Burp Suite |
| **Teste de Aceitação (UAT)** | Valida o produto com base em critérios definidos pelo usuário final. | Testes manuais / Beta testers |

---

## 🧾 4. Casos de Teste Principais (Exemplos)

### 🧍‍♂️ Usuário (Cliente ou Profissional)

| ID | Caso de Teste | Resultado Esperado |
|----|----------------|--------------------|
| TC001 | Cadastro de novo usuário | Conta criada com sucesso e email de verificação enviado |
| TC002 | Login com credenciais válidas | Acesso permitido e redirecionamento para tela inicial |
| TC003 | Login com senha incorreta | Exibição de mensagem de erro “Credenciais inválidas” |

---

### 🔍 Busca e Filtragem

| ID | Caso de Teste | Resultado Esperado |
|----|----------------|--------------------|
| TC010 | Buscar por “eletricista” | Lista de profissionais com a categoria correspondente |
| TC011 | Filtro por localização “São Paulo” | Exibe apenas profissionais na região especificada |

---

### 💬 Chat e Comunicação

| ID | Caso de Teste | Resultado Esperado |
|----|----------------|--------------------|
| TC020 | Enviar mensagem para profissional | Mensagem aparece imediatamente na conversa |
| TC021 | Mensagem offline | Mensagem armazenada e sincronizada quando o usuário voltar |

---

### 🗓️ Agendamento e Avaliação

| ID | Caso de Teste | Resultado Esperado |
|----|----------------|--------------------|
| TC030 | Criar agendamento | Serviço salvo no histórico do cliente e do profissional |
| TC031 | Avaliar profissional após serviço | Avaliação registrada e nota média atualizada |

---

## 🧱 5. Critérios de Aceitação

- Todas as funções críticas do MVP devem ser **100% funcionais**.  
- Nenhum erro de nível **crítico ou alto** pode permanecer aberto antes da publicação.  
- Todos os testes unitários e de integração devem passar com **≥ 90% de cobertura**.  
- A experiência do usuário deve estar livre de travamentos e bugs graves.  

---

## ⚙️ 6. Ambiente de Teste

| Componente | Configuração |
|-------------|---------------|
| **Frontend** | Kotlin Multiplatform (Android/iOS em modo debug) |
| **Backend** | Spring Boot (Profile: `test`) |
| **Banco de Dados** | PostgreSQL local / Testcontainers |
| **Serviços Mockados** | Pagamentos, Notificações, Geolocalização |
| **CI/CD** | GitHub Actions executando testes automatizados em cada commit |

---

## 📅 7. Cronograma de Testes

| Fase | Período | Atividades |
|------|----------|-------------|
| Planejamento | Nov/2025 | Criação de casos de teste e setup de ambiente |
| Execução (MVP) | Jan–Mar/2026 | Testes de unidade, integração e UI |
| Beta Testing | Abr–Mai/2026 | Testes de aceitação e feedback dos usuários |
| Pós-Lançamento | Jun/2026+ | Monitoramento de bugs e regressão |

---

## 🧰 8. Ferramentas de Apoio

- **JUnit / Kotest** – testes unitários Kotlin  
- **Spring Boot Test / MockMvc** – testes de API  
- **Postman / Newman** – testes manuais e coleções automatizadas  
- **JMeter / k6** – performance e carga  
- **Sentry** – monitoramento de erros em produção  
- **GitHub Actions** – automação de testes no pipeline CI/CD  

---

## 📊 9. Relatórios e Métricas

| Métrica | Descrição | Meta |
|----------|------------|------|
| Cobertura de testes | Percentual de código coberto | ≥ 90% |
| Defeitos críticos abertos | Bugs graves antes do deploy | 0 |
| Tempo médio para correção | Tempo entre identificação e correção | ≤ 3 dias |
| Satisfação dos beta testers | Média nas avaliações | ≥ 4.5 |

---

📄 **Última atualização:** 06/11/2025  
👤 **Responsável:** Equipe de Qualidade – *Labora Project*
