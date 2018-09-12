# 无菌检测 Tensorflow server
	基于 Flask、Tensorflow 和 WSGI 在 Apache 上部署的图像分析 API

## 程序结构
	程序主要分为 Apache24 库， Python 脚本。
	Apache24 库从 Apache 官网下载，为适合64位 Windows 7及以上的操作系统的Apache库，用于部署 WSGI 配置中的python Flask server。
	Python 脚本部分主要包括模型、Flask API。 模型是基于 Fine-tuned DenseNet的分类模型，输入图像，输出为分类结果（无菌、菌种1、菌种2......）。Flask API 主要包括 predict 等函数，可自行扩展编写。

## 部署步骤

- 下载(可从清华Anaconda镜像搜索) 并安装Anaconda3-4.0.0-Windows-x86_64.exe 注意选择给全部用户安装。如果系统添加环境变量失败，记得将 **%anaconda path%** 和 **%anaconda path%\Scripts** 添加到 **PATH** 环境变量中

- 安装tf和keras库，在 tf_server 文件夹下打开 powershell 输入 **pip install tensorflow==1.4.0 && pip install keras==2.1.0**

- 测试运行Flask，在 tf_server 下输入 **python tf_server.py** 看有没有在 **localhost:5000** 运行网页







- 重启 **Apache httpd** 观察 **localhost:5000/** 和 **python simple_request.py** 的预测情况，注意各部分端口和传递参数的对应

## 常见问题
- 服务启动的第一次模型运算会耗费约10几秒的时间，可能会导致调用部分的timeout，长时间运行最好第一次用 python 脚本测试


## TODO
- 从图像RGB单通道计算样品浊度。