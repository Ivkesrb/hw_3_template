# Счётчик

Настройки в `.env`: `PORT_NA_MAKE` — порт на компьютере (по умолчанию 8080), `TEKST_PRIVETA` — текст приветствия. Создание файла настроек:

```sh
cp .env.example .env
```

## SQLite

```sh
docker compose -p hw3sqlite -f sqlite.yaml up -d --build
docker compose -p hw3sqlite -f sqlite.yaml down
```

База хранится в томе `counter_data`.

## Redis

```sh
docker compose up -d --build --wait
```

Чтение и увеличение счётчика при стандартном порте:

```sh
curl http://localhost:8080/
curl -X POST http://localhost:8080/increment
```

Приложение подключается к `redis:6379` внутри сети Compose. Redis записывает изменения в том `redis_data`. Остановка проекта с сохранением данных:

```sh
docker compose down
```
