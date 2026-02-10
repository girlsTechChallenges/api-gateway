# API Gateway

API Gateway para arquitetura de microserviços utilizando Spring Cloud Gateway.

## Tecnologias

- Java 17
- Spring Boot 3.2.2
- Spring Cloud Gateway
- Spring Cloud Config
- Netflix Eureka Client
- Spring Boot Actuator
- Maven

## Dependências

- **spring-cloud-starter-gateway**: Roteamento e filtros para API Gateway
- **spring-cloud-starter-config**: Cliente para Spring Cloud Config Server
- **spring-cloud-starter-netflix-eureka-client**: Service discovery com Eureka
- **spring-boot-starter-actuator**: Monitoramento e métricas

## Executar

```bash
mvn spring-boot:run
```

## Endpoints

- Aplicação: http://localhost:8080
- Health Check: http://localhost:8080/actuator/health
- Métricas: http://localhost:8080/actuator/metrics

## Configuração

O Gateway está configurado para:
- Registrar-se no Eureka Server (localhost:8761)
- Descobrir e rotear automaticamente para serviços registrados
- Expor endpoints do Actuator para monitoramento
