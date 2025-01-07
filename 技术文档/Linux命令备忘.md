# Shell


Ctrl + A 行首  
Ctrl + E 行尾  
Ctrl + U 删除整行  
Ctrl + W 删除前面一个单词



# grep 
过滤 
```bash
docker images | grep ubuntu
```


# awk
## 打印某列
打印第 2 列内容

```bash
docker images | grep nginx | awk '{print $2}'
```



```shell
# 定义变量
API_NAME="msa-api-hello"
API_VERSION="0.0.1"
API_PORT="8101"
IMAGE_NAME="127.0.0.1:5000/com.msa/$API_NAME:$BUILD_NUMBER"
CONTAINER_NAME=$API_NAME-$API_VERSION

# 进入target目录并复制Dockerfile文件
cd $WORKSPACE/target
cp classes/Dockerfile .

# 构建Docker镜像
docker build -t $IMAGE_NAME .

# 推送Docker镜像
docker push $IMAGE_NAME

# 删除Docker容器
cid=$(docker ps | grep $CONTAINER_NAME |awk '{print $1}')
if [ x"$cid" != x ]
	then
   	docker rm -f $cid
fi

# 启动Docker容器
docker run -d -p $API_PORT:8080 --name $CONTAINER_NAME $IMAGE_NAME

# 删除Dockerfile文件
rm -f Dockerfile
```

## 按条件过滤
打印第2列大于10的行

```bash
awk '$2 > 10' file.txt
```

## 自定义分隔符
如果文件以逗号分隔（CSV 文件），可以指定分隔符：

```bash
awk -F ',' '{print $1, $3}' file.csv
```

## 加总某列
计算文件中第 2 列的总和：

```bash
awk '{sum += $2} END {print sum}' file.txt
```

## 替换内容
将文件中所有 old_text 替换为 new_text 并输出：

```bash
awk '{gsub("old_text", "new_text"); print}' file.txt
```



# xargs
管道

xargs 是一个命令构建器，将输入转换为命令行参数执行，常用于与其他命令结合使用

## 批量删除文件
从文件列表中删除所有 .log 文件：

```bash
find . -name "*.log" | xargs rm -f
```

## 与echo配合

```bash
echo "file1 file2 file3" | xargs rm
```

相当于 rm file1 & rm file2 & rm file3

## 指定参数数量
每次传递 2 个参数：

```bash
echo "1 2 3 4" | xargs -n 2 echo
# 输出:
# 1 2
# 3 4
```



# awk和xargs结合
## 筛选文件并操作
打印 file.txt 中列出的大于 100KB 的文件，并删除它们：

```bash
ls -l | awk '$5 > 102400 {print $9}' | xargs rm
```

## 替换文件名
将 file_list.txt 中列出的文件复制到 /backup：

```bash
awk '{print "cp " $0 " /backup"}' file_list.txt | bash
```

## 复杂命令组合

```bash
ls | awk '/\.txt$/' | xargs -n 1 gzip
```

# 其他命令


查看一级目录大小

```bash
du -sh *
```



查看磁盘占用

```bash
df -h
```



查看端口号被占用

```bash
lsof -i:PORT
```



杀死进程

```bash
kill -9 PID
```



tar压缩

```bash
tar -zcvf filename
```



tar解压

```bash
tar -zxvf filename
```





