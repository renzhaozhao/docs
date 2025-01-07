# 命令解析
## 示例
命令行
```bash
docker run -dit \
-v $PWD/ql/config:/ql/config \
-v $PWD/ql/log:/ql/log \
-v $PWD/ql/db:/ql/db \
-p 5600:5600 \
--name qinglong \
--hostname qinglong \
--restart always \
whyour/qinglong:latest
```

-v 挂载文件夹 
-p 开放端口

docker compose
```yaml
version: "3.3"
services:
  qinglong:
    stdin_open: true
    tty: true
    volumes:
      - $PWD/ql/config:/ql/config
      - $PWD/ql/log:/ql/log
      - $PWD/ql/db:/ql/db
    ports:
      - 5600:5600
    container_name: qinglong
    hostname: qinglong
    restart: always
    image: whyour/qinglong:latest
networks: {}

```


# 工具
- portainer
- dockge
