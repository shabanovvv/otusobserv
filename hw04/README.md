# Домашняя работа по настройке Grafana

В этой домашней работе установил Grafana последней доступной версии на виртуальную машину (VM) с Prometheus. Затем настроил Grafana и создал два дашборда для мониторинга инфраструктуры и приложения.

## Структура папок

В Grafana мы создал две папки:

1. `infra`: В этой папке находится дашборд для мониторинга инфраструктуры, такой как использование CPU, RAM, сети, диска

2. `app`: В этой папке находится дашборд для мониторинга CMS (системы управления контентом).
   ![Инфраструктуры](GAP-2/2024-05-02_08-49.png)

## Дашборд "infra"

Дашборд "infra" предоставляет обзор состояния инфраструктуры, включая следующие метрики:

- Использование ЦП <span style="color:green">(rate(node_cpu_seconds_total{mode="idle"}[5m]))</span>
- Потребление оперативной памяти <span style="color:green">(node_memory_MemAvailable_bytes / node_memory_MemTotal_bytes * 100)</span>
- Загрузка сети входящий <span style="color:green">(rate(node_network_receive_bytes_total[5m]))</span>
- Загрузка сети исходящий <span style="color:green">(rate(node_network_transmit_bytes_total[5m]))</span>
- Использование дискового пространства <span style="color:green">(100 - (node_filesystem_avail_bytes * 100 / node_filesystem_size_bytes))</span>
  ![Инфраструктуры](GAP-2/2024-05-03_11-40.png)

## Дашборд "app"

Дашборд "app" отображает ключевые метрики для мониторинга CMS, такие как:

- Костомная метрика CMS <span style="color:green">(laravel_some_counter)</span>
- HTTP-запросы <span style="color:green">(rate(prometheus_http_request_duration_seconds_sum[5m]) / rate(prometheus_http_request_duration_seconds_count[5m])))</span>
  ![Инфраструктуры](GAP-2/2024-05-03_11-40_1.png)

## Настройка

Для настройки дашбордов использоваль данные, собранные Prometheus с различных экспортеров. Визуализация метрик и создание панелей производились непосредственно в Grafana.
