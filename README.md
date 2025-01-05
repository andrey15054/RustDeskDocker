# RustDeskDocker
Self hosted teamviewr/anydesk using Docker. Rustdesk server is  your choice
The easiest way to  download and install RustDesk is to use this command

sudo docker run --name hbbs --restart unless-stopped -p 21115:21115 -p 21116:21116 -p 21116:21116/udp -p 21118:21118 -v `pwd`/docker/rustdesk:/root -td rustdesk/rustdesk-server hbbs -r "server ip address":21117

sudo docker run --name hbbr --restart unless-stopped -p 21117:21117 -p 21119:21119 -v `pwd`/docker/rustdesk:/root -td rustdesk/rustdesk-server hbbr

But you can also use next way

# Використовуємо офіційний образ RustDesk
FROM rustdesk/rustdesk-server:latest

# Встановлюємо робочу директорію
WORKDIR /root

# Команда за замовчуванням (може змінюватися при запуску контейнера)
CMD ["hbbs"]

Як запустити
Замініть server_ip_address в docker-compose.yml на IP-адресу вашого сервера.
Запустіть сервіси за допомогою команди:
bash

Копіювати код
docker-compose up -d

Перевірте, що контейнери працюють:
bash

Копіювати код
docker ps

5. Пояснення
hbbs відповідає за основний сервер.
hbbr обробляє маршрутизацію (relay server).

Всі дані зберігаються в локальному каталозі ./docker/rustdesk.
