# BookSwap Config Repository

Централизованные конфигурации для микросервисов BookSwap.

## Структура файлов

- `application.yml` - общие настройки для всех сервисов
- `auth-service.yml` - настройки Auth Service (R2DBC + PostgreSQL)
- `book-service.yml` - настройки Book Service (JPA + PostgreSQL)
- `exchange-service.yml` - настройки Exchange Service (JPA + PostgreSQL + Feign)
- `publication-service.yml` - настройки Publication Service (JPA + PostgreSQL + Feign)
- `gateway.yml` - настройки Spring Cloud Gateway
- `eureka-server.yml` - настройки Eureka Server

## Переменные окружения

Используемые переменные окружения:

- `EUREKA_URI` - URL Eureka сервера (default: http://localhost:8761/eureka/)
- `DB_HOST` - хост PostgreSQL (default: localhost)
- `DB_PORT` - порт PostgreSQL (default: 5432)
- `DB_NAME` - имя базы данных
- `DB_USER` - пользователь БД (default: bookswap)
- `DB_PASSWORD` - пароль БД (default: bookswap)
- `JWT_SECRET` - секретный ключ для JWT (минимум 32 символа)
- `CORS_ALLOWED_ORIGINS` - разрешённые CORS origins

## Использование

Config Server подтягивает конфигурации из этого репозитория:
```yaml
spring:
  cloud:
    config:
      server:
        git:
          uri: https://github.com/FreezinMoon/bookswap-config.git
          default-label: main
```

## Профили

Для разных окружений можно создавать файлы вида:
- `auth-service-dev.yml`
- `auth-service-prod.yml`

И активировать через: `spring.profiles.active=prod`