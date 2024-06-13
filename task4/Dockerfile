# Используем базовый образ Nginx
FROM nginx:latest

# создатель образа
MAINTAINER Гилфанова Э.Р.

# Обновляем список пакетов и устанавливаем необходимые пакеты (MariaDB)
RUN apt-get update -qq && \
    apt-get install -y -qq mariadb-server && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# Устанавливаем рабочую директорию
WORKDIR /var/www/html

# Устанавливаем переменные окружения
ENV MYSQL_ROOT_PASSWORD=rootpassword

# Добавляем конфигурационный файл Nginx
ADD nginx.conf /etc/nginx/nginx.conf

# Копируем файлы в контейнер
COPY . /var/www/html

# Создаем точку монтирования для данных MariaDB
VOLUME /var/lib/mysql

# Открываем порты для Nginx и MariaDB
EXPOSE 80 3306

# Команда для запуска сервера Nginx и MariaDB
CMD service mysql start && nginx -g 'daemon off;'
