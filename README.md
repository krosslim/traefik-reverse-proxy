# traefik-reverse-proxy

---

### 1. Создать сеть
```bash
docker network create traefik-proxy
```
### 2. Настроить Traefik
```bash
# Клонировать репозиторий
git clone https://github.com/krosslim/traefik-reverse-proxy.git
```
```bash
# Перейти в папку проекта
cd traefik-reverse-proxy
```
```bash
# Создать и заполнить .env файл
cp .env.example .env
```
### 2.1. Настройка .env
```bash
# Сгенерировать строку для BasicAuth (Linux/MacOS)
htpasswd -nbB admin "YourPassword" | sed -e s/\$/\$\$/g
```
```bash
# .env
LE_EMAIL=you@example.com
TRAEFIK_HOST=traefik.example.com # Заранее настроить A-запись
TRAEFIK_BASIC_USERS=admin:$$2y$$05$$...  # строка htpasswd
WHITELIST_IP=203.0.113.45/32,192.168.0.0/16
```
### 3. Запустить traefik
```bash
docker compose up --build -d
```




