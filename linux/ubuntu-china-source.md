# Ubuntu - 切换到中国源

以下方案同样适用于 WSL2 上的 Ubuntu。

## 华为云

```bash
sudo cp -a /etc/apt/sources.list /etc/apt/sources.list.bak && \
sudo sed -i "s@http://.*archive.ubuntu.com@http://repo.huaweicloud.com@g" /etc/apt/sources.list && \
sudo sed -i "s@http://.*security.ubuntu.com@http://repo.huaweicloud.com@g" /etc/apt/sources.list && \
sudo apt-get update
```

## 阿里云

```bash
sudo cp -a /etc/apt/sources.list /etc/apt/sources.list.bak && \
sudo sed -i "s@http://.*archive.ubuntu.com@http://mirrors.aliyun.com@g" /etc/apt/sources.list && \
sudo sed -i "s@http://.*security.ubuntu.com@http://mirrors.aliyun.com@g" /etc/apt/sources.list && \
sudo apt-get update
```
