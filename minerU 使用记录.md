##
```sh
pip install -U "mineru[core]" -i https://mirrors.aliyun.com/pypi/simple
```
mineru[all]是全部

## 快速配置模型源
```sh
export MINERU_MODEL_SOURCE=modelscope
```

## 下载模型
```sh
mineru-models-download
```

## 启动gradio webui 可视化前端
```sh
# 使用 pipeline/vlm-transformers/vlm-sglang-client 后端
mineru-gradio --server-name 0.0.0.0 --server-port 7860
# 或使用 vlm-sglang-engine/pipeline 后端（需安装sglang环境）
mineru-gradio --server-name 0.0.0.0 --server-port 7860 --enable-sglang-engine true
```