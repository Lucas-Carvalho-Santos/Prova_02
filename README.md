# Prova_02
# 🔐 API de Autenticação JWT - AV2 (Spring Boot 3)

## 🚀 Visão Geral

Este projeto é a continuação da API de autenticação JWT construída na AV1. Aqui, evoluímos a aplicação com práticas avançadas de segurança, testes, monitoramento e deploy.

A proposta contempla:

- Autenticação via JWT com geração e validação interna
- Proteção de endpoints com controle por roles
- Testes automatizados com JUnit e Mockito
- Testes de carga com JMeter
- Monitoramento com Actuator, Prometheus e Grafana
- Deploy com Docker e hospedagem em nuvem

---

## 📦 Tecnologias e Dependências

- ✅ Spring Boot Starter Web
- 🔐 Spring Boot Starter Security
- 🔑 Spring Boot Starter OAuth2 Resource Server
- 🗄 Spring Boot Starter Data JPA
- 💾 H2 Database (testes)
- 📚 Springdoc OpenAPI (Swagger)
- 🍬 Lombok
- 🛠 Spring Boot DevTools
- 🧪 Spring Boot Starter Test (JUnit, Mockito)
- 🩺 Spring Boot Actuator
- 📊 Prometheus + Grafana (monitoramento)
- 🐳 Docker
- ⚙️ JMeter (testes de carga)

---

## ⚙️ Configuração do Ambiente

```yaml
# src/main/resources/application.yml

server:
  port: 8080

spring:
  datasource:
    url: jdbc:h2:mem:testdb
    driver-class-name: org.h2.Driver
    username: sa
    password:
  jpa:
    hibernate:
      ddl-auto: update
    show-sql: true
  h2:
    console:
      enabled: true

jwt:
  secret: umaChaveSecretaMuitoLongaEComplexaParaAssinarTokensJWT
  expiration: 3600000

springdoc:
  swagger-ui:
    path: /swagger-ui.html
  api-docs:
    path: /v3/api-docs

management:
  endpoints:
    web:
      exposure:
        include: health,info,metrics,prometheus

🛠️ Funcionalidades Implementadas
🔐 Endpoints de Autenticação
POST /auth/login – autentica e retorna token JWT

POST /auth/register – registra novos usuários

POST /auth/validate – valida token existente

🛡️ Proteção de Endpoints com Spring Security
Apenas usuários autenticados podem acessar endpoints protegidos

Regras baseadas em roles (USER, ADMIN)

JWT validado com chave interna (HMAC SHA256)

🧩 Integração com Endpoints CRUD
Endpoints REST protegidos por JWT

Operações de leitura permitidas a usuários autenticados

Operações de escrita (POST/PUT/DELETE) restritas a ADMIN

