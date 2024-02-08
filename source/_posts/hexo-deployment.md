---
title: Hexo博客部署筆記
date: 2024-02-08 22:12:00
tags: [Hexo, Deployment, Windows, Note]
---

[Hexo](https://hexo.io/docs/) is a fast, simple and powerful blog framework. You write posts in Markdown (or other markup languages) and Hexo generates static files with a beautiful theme in seconds.

p.s. 本篇文章環境為 Windows 11 專業版.

## 預備步驟

1. 安裝 [git](https://git-scm.com/download/win).
2. 安裝 [Node.js](https://nodejs.org/en/download/).
    - 可透過安裝 [`nvs`](https://github.com/jasongin/nvs/) 來管理多個版本的 Node.js.
      - 法一 - 透過 `winget` 安裝
      ```powershell
      winget install jasongin.nvs
      ```
      - 法二 - 透過 `choco` 安裝
      ```powershell
      choco install nvs
      ```
      - 或直接從github下載msi安裝程式
    - 運行以下命令
    ```powershell
    nvs add latest
    nvs use latest
    nvs link latest
    ```
    - 正常的輸出應該是:
    ```powershell
    > nvs add latest
    Downloading [###########################################################################################] 100%
    Extracting  [###########################################################################################] 100%
    Added at: $env:LOCALAPPDATA\nvs\node\21.6.1\x64\node.exe
    To use this version now: nvs use node/21.6.1/x64
    > nvs use latest
    PATH -= C:\Program Files\nodejs
    PATH += $env:LOCALAPPDATA\nvs\node\21.6.1\x64
    > nvs link latest
    $env:LOCALAPPDATA\nvs\default -> $env:LOCALAPPDATA\nvs\node\21.6.1\x64
    User profile PATH += $env:LOCALAPPDATA\nvs\default
    ```
    - 使用 `node -v` 來檢驗是否正確安裝Node.js.
    ```powershell
    > node -v
    v21.6.1
    ```

## 安裝 Hexo

### Install Hexo
Once all the requirements are installed, you can install Hexo with npm:
```powershell
$ npm install -g hexo-cli
```

### Advanced installation and usage
Advanced users may prefer to install and use hexo package instead.
```powershell
$ npm install hexo
```
Once installed, you can run Hexo in two ways:
```powershell
npx hexo <command>
```
Linux users can set relative path of node_modules/ folder:
```powershell
echo 'PATH="$PATH:./node_modules/.bin"' >> ~/.profile
```
then run Hexo using `hexo <command>`

### 所以

我選擇直接 `npm install -g hexo-cli`.

看到 `added 54 packages in 8s` 就算成功了.

## 開始開發

使用如下命令初始化你的項目資料夾: 
```powershell
> E:; cd projects # 切換到 projects 資料夾
> hexo init gang-no-blog
INFO  Cloning hexo-starter https://github.com/hexojs/hexo-starter.git
fatal: unable to access 'https://github.com/hexojs/hexo-starter.git/': Recv failure: Connection was reset
WARN  git clone failed. Copying data instead
INFO  Install dependencies
INFO  Start blogging with Hexo!
> cd gang-no-blog
```

測試一下!! 
運行 `hexo generate` 命令, 然後在VSCode中切換到 `public` 資料夾, 就可以使用live server預覽生成的博客了.

## 部署到 GitHub Pages

跟著這篇[官方教程](https://hexo.io/docs/github-pages)走就好👌