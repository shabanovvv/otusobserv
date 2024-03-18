# Prometheus и экспорт метрик

Все реализовано через docker-compose.yml
в нем было установлены следующие контейнеры:
1. Веб сервер Nginx
2. Php-fpm 8.2
3. БД PostgreSql
4. Prometheus
5. Экспортер в Prometheus Nginx
6. Экспортер в Prometheus Php-fpm
7. Экспортер в Prometheus Postgres
8. Экспортер в Prometheus Blackbox
9. Экспортер в Prometheus Node

Также были добавлены файлы конфигураций в соотвествующие папки.
