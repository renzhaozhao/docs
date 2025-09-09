
## 虚拟环境
```sh
# 创建虚拟环境
python -m venv .
# 进入虚拟环境
source bin/activate
# 安装依赖
pip install -r requirements.txt
# 启动
python main.py --listen 0.0.0.0 --port 8188
```

## pip install 国内源
```sh
pip3 install -r requirements.txt -i https://pypi.tuna.tsinghua.edu.cn/simple
```
