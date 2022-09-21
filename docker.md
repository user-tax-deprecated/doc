docker-compose up -d

查看日志
docker logs pg_1

进入数据库服务器
docker exec -it  pg_1 /bin/bash
