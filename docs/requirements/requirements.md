# 📋 Labora – Documento de Requisitos

## 1. Introdução

Este documento descreve os **requisitos funcionais e não funcionais** do aplicativo **Labora**, uma plataforma multiplataforma desenvolvida em **Kotlin Multiplatform** com backend em **Spring Boot**, cujo objetivo é conectar **profissionais autônomos** a **clientes** que buscam serviços locais.

O foco é garantir clareza sobre o escopo, as funcionalidades esperadas e as restrições técnicas, servindo como base para o desenvolvimento, testes e manutenção do sistema.

---

## 2. Escopo do Sistema

O **Labora** permitirá que:
- **Clientes** encontrem profissionais autônomos de forma rápida, filtrando por tipo de serviço e localização.  
- **Profissionais** divulguem seus serviços e recebam solicitações diretamente pelo aplicativo.  
- Ambas as partes possam **se comunicar, agendar e avaliar** os serviços prestados.  

Futuramente, o aplicativo oferecerá **pagamentos integrados**, **notificações em tempo real** e **planos premium** para profissionais.

---

## 3. Requisitos Funcionais

| ID | Requisito | Descrição | Prioridade |
|----|------------|------------|-------------|
| RF001 | Cadastro de Usuário | O sistema deve permitir o cadastro de clientes e profissionais, com validação de dados básicos (nome, email, telefone, senha). | Alta |
| RF002 | Login e Autenticação | O sistema deve permitir autenticação via email/senha e integração futura com redes sociais. | Alta |
| RF003 | Gerenciamento de Perfil | Usuários poderão criar e editar perfis com foto, descrição e área de atuação. | Alta |
| RF004 | Busca de Profissionais | Clientes poderão buscar profissionais por categoria e localização. | Alta |
| RF005 | Sistema de Mensagens | Clientes e profissionais poderão se comunicar via chat interno. | Média |
| RF006 | Agendamento de Serviços | O sistema deve permitir que clientes agendem serviços com data e hora. | Média |
| RF007 | Avaliação de Serviços | Após a conclusão, o cliente poderá avaliar o profissional com nota e comentário. | Média |
| RF008 | Histórico de Serviços | Usuários poderão visualizar histórico de serviços realizados. | Média |
| RF009 | Notificações | O sistema enviará notificações sobre novas mensagens e agendamentos. | Baixa (Futura) |
| RF010 | Pagamentos Integrados | O sistema permitirá pagamentos via Pix ou cartão, com registro seguro da transação. | Baixa (Futura) |
| RF011 | Planos Premium | O sistema deve oferecer planos pagos para profissionais, com benefícios adicionais. | Baixa (Futura) |
| RF012 | Recomendação Inteligente | O sistema recomendará profissionais com base em histórico e localização. | Baixa (Futura) |

---

## 4. Requisitos Não Funcionais

| ID | Categoria | Descrição | Prioridade |
|----|------------|------------|-------------|
| RNF001 | Desempenho | O sistema deve suportar no mínimo 10.000 usuários simultâneos. | Alta |
| RNF002 | Segurança | Todos os dados sensíveis devem ser armazenados criptografados (senha com bcrypt). | Alta |
| RNF003 | Disponibilidade | O sistema deve estar disponível 99% do tempo mensal. | Alta |
| RNF004 | Escalabilidade | O backend deve permitir expansão horizontal conforme a base de usuários crescer. | Média |
| RNF005 | Usabilidade | A interface deve ser responsiva e intuitiva em dispositivos Android e iOS. | Alta |
| RNF006 | Portabilidade | O aplicativo deve funcionar com o mesmo código base em Android e iOS. | Alta |
| RNF007 | Manutenibilidade | O código deve seguir padrões de clean code e arquitetura modular (KMP + Spring Boot). | Média |
| RNF008 | Auditoria | O sistema deve registrar logs de autenticação, agendamento e pagamento. | Média |
| RNF009 | Conformidade | O sistema deve seguir a LGPD (Lei Geral de Proteção de Dados). | Alta |

---

## 5. Requisitos de Interface

- **Interface do Cliente:**
  - Tela inicial com barra de busca e categorias.  
  - Lista de profissionais com foto, nome, avaliação e distância.  
  - Tela de chat e agendamento.  
  - Tela de avaliação e histórico de serviços.  

- **Interface do Profissional:**
  - Tela de cadastro e gerenciamento de serviços oferecidos.  
  - Visualização de solicitações e mensagens.  
  - Tela de avaliações recebidas e estatísticas básicas.

---

## 6. Requisitos de Dados

| Entidade | Descrição | Campos Principais |
|-----------|------------|------------------|
| Usuário | Representa clientes e profissionais. | id, nome, email, senha, tipo (cliente/profissional) |
| Perfil | Informações complementares do usuário. | foto, descrição, especialidade, localização |
| Serviço | Registro de solicitações de serviços. | id, cliente_id, profissional_id, data, status |
| Mensagem | Comunicação entre cliente e profissional. | id, remetente_id, destinatário_id, conteúdo, timestamp |
| Avaliação | Registro de feedbacks. | id, serviço_id, nota, comentário |

---

## 7. Restrições

- O aplicativo será inicialmente lançado para **Android e iOS**.  
- O sistema backend utilizará **Spring Boot** com **PostgreSQL** (ou MongoDB, conforme evolução).  
- Os serviços de hospedagem serão implementados na **DigitalOcean** (com possibilidade de migração para AWS).  

---

## 8. Dependências Externas

- API de mapas e geolocalização (Google Maps ou OpenStreetMap).  
- Serviço de autenticação (Firebase Auth ou Keycloak).  
- Gateway de pagamento (Pagar.me, Stripe, ou integração via OpenPix).  
- Serviço de notificações (Firebase Cloud Messaging).  

---

## 9. Critérios de Aceitação

- Um cliente deve conseguir cadastrar-se, buscar profissionais e enviar mensagens.  
- Um profissional deve conseguir receber solicitações e responder.  
- Um serviço deve poder ser agendado, concluído e avaliado.  
- Nenhum dado sensível pode ser transmitido sem criptografia (HTTPS/TLS).  
- O sistema deve continuar funcional mesmo com 1000 requisições simultâneas.

---

## 10. Versão do Documento

- **Versão:** 1.0  
- **Data:** Novembro de 2025  
- **Autor:** Raul Nunes  
- **Projeto:** Labora  
