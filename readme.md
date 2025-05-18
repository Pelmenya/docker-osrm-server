### Шаги для использования docker-compose.yml:

### Скачать дамп OSM данных

Перейдите на сайт [Geofabrik](https://download.geofabrik.de/russia.html) и выберите нужный вам регион, чтобы загрузить актуальный дамп данных в формате `.osm.pbf`.
Поместите его в папку osm проекта

Структура папок:

Убедитесь, что у вас есть следующая структура:

```bash
/path/to/project
├── docker-compose.yml
└── osm
    └── russia-latest.osm.pbf

```
Замените /path/to/project на путь к вашей рабочей директории.

## Запуск Docker Compose:

Перейдите в директорию, где находится ваш docker-compose.yml файл, и выполните команду:
```bash
docker-compose up
```

Это запустит процесс извлечения, контрактирования и запуска OSRM сервера.

## Тестирование:

После завершения подготовки данных и запуска сервера, вы можете протестировать его с помощью HTTP-запроса:
```bash
curl "http://localhost:5000/route/v1/driving/37.6173,55.7558;30.3158,59.9398?overview=false"
```

Это запросит маршрут от Москвы до Санкт-Петербурга.

## Для пересборки данных из файла .osm.pbf, удаляем флаг /data/ready

```bash
docker-compose exec osrm-osrm-prepare-1 rm /data/ready
```
