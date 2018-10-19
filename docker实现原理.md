##docker 实现原理
```
# 文章出处 https://draveness.me/docker?from=singlemessage&isappinstalled=0
```
- Docker 通过 Linux 的命名空间实现了网络的隔离，又通过 iptables 进行数据包转发，让 Docker 容器能够优雅地为宿主机器或者其他容器提供服务
