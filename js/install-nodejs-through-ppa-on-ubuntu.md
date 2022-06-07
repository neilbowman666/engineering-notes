# 在 Ubuntu 上通过 PPA 安装 NodeJS

## 问题来源

1. 通过 `apt-get` 所安装的软件包

## 植入 PPA 源

```bash
curl -sL https://deb.nodesource.com/setup_16.x | sudo -E bash -
```

注意：您可以更改上面 URL 部分的版本号来植入您需要的 NodeJS 版本的 PPA。 

## 安装 NodeJS

```bash
sudo apt install nodejs
```

安装完成

注意：NodeJS 的部分功能需要您有编译环境，请使用下面的命令在公库安装。

```bash
sudo apt-get install gcc g++ make
```

## 安装 Yarn

```bash
curl -sL https://dl.yarnpkg.com/debian/pubkey.gpg | gpg --dearmor | sudo tee /usr/share/keyrings/yarnkey.gpg >/dev/null

echo "deb [signed-by=/usr/share/keyrings/yarnkey.gpg] https://dl.yarnpkg.com/debian stable main" | sudo tee /etc/apt/sources.list.d/yarn.list

sudo apt-get update && sudo apt-get install yarn
```

## NPM 配置中国源

[链接](./npm-china-srouce.md)

## NPM 自升级

```bash
npm install -g npm@latest
```
