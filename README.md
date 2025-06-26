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
```

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


Endpoints REST protegidos por JWT

## ⚙️ Configuração do Ambiente

🧪 Testes Automatizados
JUnit 5 + MockMvc

Testes de autenticação e acesso

Validação de tokens

Verificação de acesso negado

bash
Copiar
Editar
./mvnw test
📈 Testes de Carga com JMeter
Como Rodar:
Abra o JMeter e crie um Thread Group (ex: 200 usuários, 10 loops)

Adicione um HTTP Request para POST /auth/login

Defina parâmetros: username=admin, password=123456

Adicione os listeners:

Summary Report

View Results Tree

Execute e analise:

✅ Throughput

⏱️ Tempo Médio de Resposta

❌ % de Erros

Arquivo JMX: jmeter-tests/login_stress_test.jmx

📚 Documentação da API
Acesse: http://localhost:8080/swagger-ui.html

Documentação interativa dos endpoints

Suporte a autenticação Bearer JWT via Swagger UI

🩺 Monitoramento da API
Endpoints disponíveis via Spring Boot Actuator:
/actuator/health

/actuator/info

/actuator/metrics

/actuator/prometheus

Prometheus
Configurado para raspar métricas da API

Conecta no endpoint /actuator/prometheus

Grafana
Dashboards com métricas em tempo real:

Requisições por segundo

Tempo médio de resposta

Uso de CPU e memória

🐳 Docker e Deploy
Dockerfile
dockerfile
Copiar
Editar
FROM eclipse-temurin:17-jdk-alpine
COPY target/auth-api.jar app.jar
ENTRYPOINT ["java", "-jar", "/app.jar"]
Build e Execução
bash
Copiar
Editar
./mvnw clean package
docker build -t auth-api .
docker run -p 8080:8080 auth-api
Hospedagem gratuita recomendada
Render – Deploy direto do GitHub

Railway – Suporte para Spring Boot e Docker

🔧 Como Executar Localmente
Clone o repositório:

bash
Copiar
Editar
git clone https://github.com/seu-usuario/auth-api-av2.git
cd auth-api-av2
Rode o projeto:

bash
Copiar
Editar
./mvnw spring-boot:run
Acesse:

Swagger UI: http://localhost:8080/swagger-ui.html

H2 Console: http://localhost:8080/h2-console

👥 Usuários Padrão
Usuário	Senha	Role
admin	123456	ADMIN
user	password	USER

Operações de leitura permitidas a usuários autenticados

Operações de escrita (POST/PUT/DELETE) restritas a ADMIN

---

