# API Gateway

API Gateway para arquitetura de microserviços utilizando Spring Cloud Gateway.

## Tecnologias

- Java 17
- Spring Boot 3.4.2
- Spring Cloud 2024.0.0
- Spring Cloud Gateway
- Spring Cloud Config
- Netflix Eureka Client
- Spring Boot Actuator
- Maven
- Docker

## Dependências

- **spring-cloud-starter-gateway**: Roteamento e filtros para API Gateway
- **spring-cloud-starter-config**: Cliente para Spring Cloud Config Server
- **spring-cloud-starter-netflix-eureka-client**: Service discovery com Eureka
- **spring-boot-starter-actuator**: Monitoramento e métricas

## Executar

### Local

```bash
mvn spring-boot:run
```

### Docker

```bash
# Build da imagem
docker build -t api-gateway .

# Executar container
docker run -p 8080:8080 api-gateway
```

## Endpoints

- Aplicação: http://localhost:8080
- Health Check: http://localhost:8080/actuator/health
- Info: http://localhost:8080/actuator/info
- Métricas: http://localhost:8080/actuator/metrics

## Rotas Configuradas

O API Gateway roteia as seguintes requisições:

| Serviço | Caminho | Destino | Ações |
|---------|---------|---------|-------|
| check-health-service | `/api/v1/goals/**` | `lb://check-health-service` | StripPrefix=2 |

## Configuração

O Gateway está configurado para:
- **Service Discovery**: Registrar-se no Eureka Server (`discovery-service:8761`)
- **Config Server**: Importar configurações do Config Server (`config-service:8888`) de forma opcional
- **Load Balancing**: Rotear automaticamente para serviços registrados usando `lb://`
- **Actuator**: Expor endpoints de `health`, `info` e `metrics` para monitoramento
- **Preferência IP**: Usar endereço IP para registro no Eureka

### Arquivos de Configuração

- `application.yml`: Configuração principal do gateway
- `config/api-gateway.yml`: Configuração adicional de rotas
