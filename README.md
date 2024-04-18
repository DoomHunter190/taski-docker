## Описание:
Проект таск-трекера для практики развертывания на сервере и настройки CI&CD. Репозиторий содержит код Docker-контейнеров для развертывания приложения на сервере.
## Как запустить проект:
Для полноценного развертывания вам понадобится свой сервер.
- Клонировать репозиторий.
- Локально отредактируйте файл gateway/nginx.conf и в строке server_name впишите свой IP
- Подключитесь к вашему серверу с помощью SSH:
```
ssh <server user>@<server IP>
```

- Установите Docker на вашем сервере:
```
sudo apt install docker.io
```

- Установите Docker Compose (для Linux):
```
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```

- Получите разрешения для docker-compose:
```
sudo chmod +x /usr/local/bin/docker-compose
```

- Создайте директорию проекта (желательно в вашей домашней директории):
```
mkdir Docker-notes && cd Docker-notes/
```

- Скопируйте файлы из 'infra/' (на вашем локальном компьютере) на ваш сервер:
```
scp -r infra/* <server user>@<server IP>:/home/<server user>/Docker-notes/
```

- Cоздайте .env файл:
```
mv .env.example .env
```

- И впишите в него:
```
POSTGRES_DB=<имя базы данных postgres>
POSTGRES_USER=<пользователь бд>
POSTGRES_PASSWORD=<пароль>
DB_HOST=db
DB_PORT=5432
SECRET_KEY=секретный ключ проекта django>
DEBUG=False
ALLOWED_HOSTS=localhost,127.0.0.1,158.160.70.1,0.0.0.0,<IP или название вашего сервера>
```

- Запустите docker-compose:
```
sudo docker-compose -f docker-compose.production.yml up -d
```

Автор | Почта
------------- | -------------
[Doomhunter190](https://github.com/DoomHunter190) | <small>[maximportnov9999@gmail.com](maximportnov9999@gmail.com)
