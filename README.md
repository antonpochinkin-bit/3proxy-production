# 3Proxy Production System

Производственная система 3proxy с балансировкой нагрузки через Nginx в Docker контейнерах.

## Возможности

- Балансировка нагрузки между несколькими инстансами 3proxy
- Высокая доступность - система работает при падении одного из прокси
- Аутентификация для защищенных прокси
- Публичные прокси без аутентификации
- Веб-интерфейсы для мониторинга
- Простое развертывание через Docker Compose

## Архитектура

Клиенты -> Nginx Балансировщик -> {3proxy1, 3proxy2}

## Быстрый старт

### Требования
- Docker
- Docker Compose

### Установка

```bash
git clone https://github.com/antonpochinkin-bit/3proxy-production.git
cd 3proxy-production
docker-compose up -d
docker-compose ps


Доступные сервисы
Прокси-серверы

    HTTP/HTTPS с аутентификацией: localhost:18080

        Логин: testuser

        Пароль: password123

    SOCKS5 с аутентификацией: localhost:11080

        Логин: testuser

        Пароль: password123

    Публичный HTTP/HTTPS: localhost:13128 (без аутентификации)

    Публичный SOCKS5: localhost:11081 (без аутентификации)

Веб-интерфейсы

    Мониторинг Nginx: localhost:8080

    Админка 3proxy1: localhost:19999

        Логин: admin

        Пароль: admin123

    Админка 3proxy2: localhost:29999

        Логин: admin

        Пароль: admin123

Структура проекта

    docker-compose.yml - Docker оркестрация

    config/3proxy.cfg - Конфигурация 3proxy

    config/passwd - Данные пользователей

    nginx/nginx.conf - Конфигурация балансировщика Nginx

    3proxy/Dockerfile - Docker образ 3proxy

Тестирование
bash

curl -x http://testuser:password123@localhost:18080 http://ifconfig.me
curl -x http://localhost:13128 http://ifconfig.me
