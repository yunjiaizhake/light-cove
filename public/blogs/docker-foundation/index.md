# 一、镜像（image）相关
**docker images [参数]**
- -a, --all：显示所有镜像（包括中间层、隐藏镜像）
- -q, --quiet：仅输出镜像 ID
- -qa：组合参数，输出所有镜像的 ID
- --filter, -f：过滤显示镜像
- --no-trunc：显示完整的镜像 ID（不截断）

**docker pull [参数]**
- 基础用法：docker pull 镜像名:标签
- -a：拉取所有标签版本

**docker rmi [参数]**
- -f, --force：强制删除镜像
- 无其他参数，直接使用 docker rmi 镜像ID/名称

# 二、容器（container）相关
**docker ps [参数]**
- -a, --all：显示所有容器（包括未运行）
- -q, --quiet：仅输出容器 ID
- -qa：组合参数，输出所有容器 ID
- -l, --latest：显示最近创建的容器
- -n，数字：显示最近 n 个容器
- --no-trunc：显示完整容器 ID

**docker start [参数]**
- 无额外常用参数，直接启动容器

**docker stop [参数]**
- 无额外常用参数，直接停止容器

**docker restart [参数]**
- 无额外常用参数，直接重启容器

**docker rm [参数]**
- -f, --force：强制删除运行中的容器
- -v, --volumes：删除容器同时删除挂载的数据卷

# 三、run 创建/运行容器（最核心）
**docker run [参数] 镜像名 [命令]**
- -d, --detach：后台运行容器
- -it：交互式终端（必须组合使用）
  -i：保持标准输入打开
  -t：分配虚拟终端
- -p, --publish：端口映射（主机端口:容器端口），小写 p
- -P, --publish-all：随机映射所有端口，大写 P
- --name：指定容器名称
- --hostname：设置容器主机名
- --restart=always：容器崩溃/重启后自动启动
- -v, --volume：目录/文件挂载（主机路径:容器路径）
- -e, --env：设置环境变量
- --network：指定容器使用的网络
- -w, --workdir：指定容器工作目录
- -u, --user：指定运行用户
- --rm：容器停止后自动删除
- --privileged：给容器最高权限（慎用）

# 四、exec 进入容器
**docker exec [参数] 容器ID 命令**
- -it：交互式进入终端
- -d：后台执行命令
- -w：指定工作目录
- -u：指定执行用户

# 五、logs 查看日志
**docker logs [参数] 容器ID**
- -f, --follow：实时跟踪日志输出
- --tail 数字：只显示最后 n 行日志
- -t, --timestamps：显示日志时间戳
- --since：显示指定时间之后的日志

# 六、网络（network）
**docker network ls [参数]**
- -a：显示所有网络
- -q：仅显示网络 ID

**docker network create [参数]**
- --driver：指定网络驱动（bridge/host/none）
- --subnet：指定子网
- --gateway：指定网关

# 七、数据卷（volume）
**docker volume ls [参数]**
- -q：仅显示卷 ID
- -f：过滤

**docker volume rm [参数]**
- -f：强制删除

# 八、系统管理
**docker info**：查看 Docker 系统信息 

**docker version**：查看版本详情

**docker system df**：查看磁盘占用

**docker system prune [参数]**：清理无用资源
  -a：清理所有未使用镜像
  -f：强制清理不提示

# 九、批量操作常用组合
**$(docker images -qa)**：获取所有镜像 ID

**$(docker ps -qa)**：获取所有容器 ID
