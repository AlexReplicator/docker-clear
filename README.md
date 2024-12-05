# Гайд по полной очистке Docker

![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white) ![GitHub](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white) ![Shell Script](https://img.shields.io/badge/Shell_Script-121011?style=for-the-badge&logo=gnu-bash&logoColor=white)

Этот небольшой гайд поможет вам удалить все данные Docker на вашем компьютере. Следуйте этим шагам, чтобы полностью очистить Docker.

## Шаги:

1. **Остановите все запущенные контейнеры:**
    
    `docker stop $(docker ps -aq)`
    
2. **Удалите все остановленные контейнеры:**
    
    `docker rm $(docker ps -aq)`
    
3. **Удалите все образы:**
    
    `docker rmi $(docker images -q)`
    
4. **Удалите все неиспользуемые данные (включая тома и сети):**
    
    `docker builder prune -a --force docker volume rm $(docker volume ls -q) docker system prune -a --volumes --force docker network prune --force`
    

## Цельный кода

Вот код который выполняет сразу все команды сверху

```
# Остановите все запущенные контейнеры
docker stop $(docker ps -aq)

# Удалите все остановленные контейнеры
docker rm $(docker ps -aq)

# Удалите все образы
docker rmi $(docker images -q)

# Удалите все неиспользуемые данные (включая тома и сети)
docker builder prune -a --force
docker volume rm $(docker volume ls -q)
docker system prune -a --volumes --force
docker network prune --force
```
