# 智能车考核 M0 项目

## M0-1 搭建开发环境的经历

### 1. 环境搭建
- 系统：一开始尝试双系统，因为教程太老，跟着做失败了，决定选择WSL2 Ubuntu 22.04
- 下载完后使用鱼香ROS一键换源，替换为国内源（中科大）。
- 安装 ROS2 Humble 桌面版成功。
- VScode连接wsl成功
- 成功创建文件夹和git仓库
- 写了第一次README并提交给git
- 创建了gitignore
- 下好了numpy等工具及WSL在VScode里的python等插件
-  启动了SSH的服务



### 2. 踩坑记录
- **踩坑1：网络中断导致 ROS2 安装失败**
  - 在教室下载，没有电源，加上校园网卡顿，第一次失败，失败后上网找教程如何继续下载下载一般的软件，手动后成功  。
- **踩坑2：不要找太老的教程，因为版本不一样，会出现莫名其妙的错误。**
- **踩坑3VS Code 连接 WSL 网络卡顿**
  - 现象：VS Code 下载服务器组件卡死报错。
  - 解决：换手机热点下载，并点击了非常厉害的VScode自己蹦出来的`Reopen Folder in WSL` 成功连入。
- **踩坑4：忘记设置gitignore了，还好及时收手。**
- **踩坑5：以为是网络不好，其实没装服务端。**
- **现象**：执行 `ssh localhost` 时报错 `connect to host localhost port 22: Connection refused`。
- **原因**：Linux 默认只装了 SSH 客户端（openssh-client），未安装并启动 SSH 服务端（openssh-server）。
- **解决**：
  1. 执行 `sudo apt install openssh-server -y` 安装服务端。
  2. 执行 `sudo service ssh start` 启动服务。
  3. 再次执行 `ssh localhost` 成功进入远程终端。