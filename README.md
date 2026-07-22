
<p align="center">
  <h1>pixlib 图像处理工具包</h1>
  <a href="https://pypi.org/project/pixlib/"><img src="https://img.shields.io/pypi/v/pixlib.svg" alt="PyPI version"></a>
  <a href="https://pypi.org/project/pixlib/"><img src="https://img.shields.io/badge/Python-3.8~3.14-3776AB?logo=python&logoColor=white" alt="Python"></a>
  <a href="https://github.com/zhenzi0322/pixlib/blob/main/LICENSE"><img src="https://img.shields.io/pypi/l/pixlib.svg" alt="License"></a>
  <a href="https://tool.long920.cn/pixlib"><img src="https://app.readthedocs.org/projects/zhenzi0322-tool/badge/?version=latest" alt="Documentation Status"></a>
</p>

> 一个轻量级的 Python 图像处理库，专为 AI 图像生成工作流设计。提供纯色图检测、图片有效性校验、URL 图片下载、文件哈希重命名、MD5 计算等实用功能。

### 主要特性

- **纯色图检测** (`ImageTool.is_plain_gray`) - 通过 7 个维度综合判定图片是否为纯色图
- **图片有效性校验** (`ImageTool.is_valid_image`) - 检测图片是否损坏或不完整
- **URL 图片下载** (`ImageTool.get_img_url_io`) - 从 URL 获取图片，支持指数退避重试
- **文件哈希重命名** (`ImageTool.process_single_image`) - 以文件 MD5 命名图片，自动去重
- **MD5 计算** (`utils.str_to_md5`) - 支持字符串、bytes、文件路径
- **随机字符串** (`utils.generate_random_lowercase`) - 生成随机小写字母

## 安装

```bash
pip install pixlib
```

## 使用示例

```python
import pixlib

# 纯色图检测
is_gray, metrics, msg = pixlib.ImageTool.is_plain_gray(image_bytes)

# 图片有效性校验
try:
    pixlib.ImageTool.is_valid_image(image_bytes, task_id="abc123")
except Exception as e:
    print(e.extra_data)

# URL 下载图片
im_io = pixlib.ImageTool.get_img_url_io("https://example.com/img.png")

# MD5 计算
pixlib.utils.str_to_md5("hello")
pixlib.utils.str_to_md5("/path/to/image.png")
```
