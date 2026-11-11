# Zabbix 8.0 仪表盘模板

**简体中文** · [English](README_en.md)

本项目提供 23 套可导入的 Zabbix 8.0 全局仪表盘。每套均有简体中文和英文源文件，可按需导入，也可同时导入两个版本。

## 导入与使用

1. 在 Zabbix 打开 **仪表盘 → 所有仪表盘 → 导入**，选择下方对应语言的源文件。首次导入启用**创建缺失**。重新导入时，启用**更新现有**会替换同名仪表盘的页面和组件。
2. 为监控目标关联对应的监控模板，并确认主机标签及采集状态。文件系统、端口、容器等图表需要相应的自动发现监控项和历史数据。
3. 打开仪表盘，在各页签左侧选择主机或目标。通过右上角的时间选择器调整趋势图范围。自定义标题随导入版本显示，系统菜单和告警级别随用户界面语言显示。

## 模板介绍

### 1. Linux 服务器监控

适合日常巡检。交互式概览随所选主机显示处理器使用率、可用内存、网卡流量和告警级别分布。蜂窝图和处理器排行用于对照多台主机。

关联 Linux 系统监控模板，主机标签为 `target=linux`。网卡曲线依赖接口自动发现。

[简体中文源文件](zh-CN/linux-server-monitoring.zh-CN.yaml) · [英文源文件](en/linux-server-monitoring.en.yaml)

![Linux 服务器监控简体中文版截图](images/linux-server-monitoring.zh-CN.png)

![Linux 服务器监控英文版截图](images/linux-server-monitoring.en.png)

### 2. Linux 主机性能分析

适合排查单台主机的性能瓶颈。主机概览页显示系统负载、处理器与输入输出等待、内存、交换空间和进程。存储与网络页显示挂载点容量、空闲索引节点、磁盘吞吐与等待时间，以及网卡流量、错误和丢弃包。

关联 Linux 系统监控模板，主机标签为 `target=linux`。存储与网络页需要相应的自动发现数据。

[简体中文源文件](zh-CN/linux-host-performance.zh-CN.yaml) · [英文源文件](en/linux-host-performance.en.yaml)

![Linux 主机性能分析简体中文版截图](images/linux-host-performance.zh-CN.png)

![Linux 主机性能分析英文版截图](images/linux-host-performance.en.png)

### 3. Zabbix 服务端全景状态

平台健康页显示当前实例的系统信息，以及所选主机的采集速率、数据库写入速率、队列、进程繁忙率和缓存使用率。服务器资源页显示处理器、内存、负载、文件系统、磁盘与网卡。

主机标签为 `target=zabbix`。平台健康页依赖 Zabbix 服务端健康模板，服务器资源页依赖 Linux 系统监控模板。

[简体中文源文件](zh-CN/zabbix-server-status.zh-CN.yaml) · [英文源文件](en/zabbix-server-status.en.yaml)

### 4. Windows 系统监控

系统与计算页显示采集代理可用性、处理器时间分布与队列、内存、分页文件、进程和线程。存储与网络页显示卷空间、磁盘请求等待、网卡流量和错误。

关联 Windows 系统监控模板，主机标签为 `target=windows`。卷、磁盘和网卡指标依赖自动发现。

[简体中文源文件](zh-CN/windows-system.zh-CN.yaml) · [英文源文件](en/windows-system.en.yaml)

### 5. SNMP 网络设备与端口

查看设备可用性、运行时长和端口状态，通过收发流量、错误包和丢弃包定位异常端口。页面还显示探测往返时间和丢包率。

关联通用 SNMP 网络设备模板，主机标签为 `target=generic`，并配置 SNMP 接口及端口自动发现。

[简体中文源文件](zh-CN/snmp-network-device.zh-CN.yaml) · [英文源文件](en/snmp-network-device.en.yaml)

### 6. ICMP 可达性与延迟

查看所选目标的可达状态、往返时间和丢包率趋势。丢包排行用于比较当前用户有权限查看的匹配目标。

关联 ICMP 探测模板，主机标签为 `target=icmp`，并配置可探测的目标地址。

[简体中文源文件](zh-CN/icmp-reachability.zh-CN.yaml) · [英文源文件](en/icmp-reachability.en.yaml)

![ICMP 可达性与延迟简体中文版截图](images/icmp-reachability.zh-CN.png)

![ICMP 可达性与延迟英文版截图](images/icmp-reachability.en.png)

### 7. 网站浏览器性能

将页面加载时间拆分为域名解析、连接、加密握手、请求、响应和文档就绪等阶段，同时显示传输大小与正文大小。

关联网站浏览器监控模板，主机标签为 `target=browser`。需要可用的浏览器驱动及已配置的网站地址。

[简体中文源文件](zh-CN/website-browser-performance.zh-CN.yaml) · [英文源文件](en/website-browser-performance.en.yaml)

### 8. TLS 证书有效期

按到期时间查找最早到期的证书，并查看所选主机的证书校验结果、生效时间和签名算法。

关联网站证书监控模板，主机标签为 `target=certificate`。需要通过 Zabbix 采集代理 2 获取证书，并完成证书发现。

[简体中文源文件](zh-CN/tls-certificate-inventory.zh-CN.yaml) · [英文源文件](en/tls-certificate-inventory.en.yaml)

### 9. MySQL 性能与复制

负载与连接页显示查询速率、连接线程、慢查询和网络吞吐。InnoDB 与复制页显示缓冲池效率、行锁等待、库容量和复制延迟。

关联基于 Zabbix 采集代理 2 的 MySQL 模板，主机标签为 `target=mysql`。库容量依赖数据库发现，复制延迟应在副本上查看。

[简体中文源文件](zh-CN/mysql-operations.zh-CN.yaml) · [英文源文件](en/mysql-operations.en.yaml)

### 10. PostgreSQL 性能与复制

会话与事务页显示连接状态、提交与回滚速率、缓存命中率、死锁和冲突。容量与复制页显示各库容量、锁数量、复制延迟及字节差。

关联基于 Zabbix 采集代理 2 的 PostgreSQL 模板，主机标签为 `target=postgresql`。分库和分应用指标依赖相应发现规则。

[简体中文源文件](zh-CN/postgresql-operations.zh-CN.yaml) · [英文源文件](en/postgresql-operations.en.yaml)

### 11. Redis 缓存与持久化

查看客户端连接与阻塞、内存与常驻集、网络吞吐、命中和未命中累计值，以及键的过期、淘汰与各逻辑库键数。页面也显示最近一次持久化操作耗时。

关联基于 Zabbix 采集代理 2 的 Redis 模板，主机标签为 `target=redis`。逻辑库键数依赖数据库发现。

[简体中文源文件](zh-CN/redis-operations.zh-CN.yaml) · [英文源文件](en/redis-operations.en.yaml)

### 12. Docker 引擎与容器

查看引擎状态、容器数量、镜像与卷占用。按容器查看处理器、内存、网络、累计重启次数和健康状态。

关联基于 Zabbix 采集代理 2 的 Docker 模板，主机标签为 `target=docker`。采集端需要访问 Docker 接口并启用容器发现。

[简体中文源文件](zh-CN/docker-runtime.zh-CN.yaml) · [英文源文件](en/docker-runtime.en.yaml)

![Docker 引擎与容器简体中文版截图](images/docker-runtime.zh-CN.png)

![Docker 引擎与容器英文版截图](images/docker-runtime.en.png)

### 13. VMware vSphere 主机与虚拟机

ESXi 主机页显示处理器、内存、网络和数据存储延迟。虚拟机页显示处理器调度等待、来宾与宿主内存、虚拟磁盘延迟和来宾文件系统空间。

关联 VMware 宿主机和来宾机监控模板。宿主机使用 `target=vmware-hypervisor`，虚拟机使用 `target=vmware-guest`。

[简体中文源文件](zh-CN/vmware-vsphere.zh-CN.yaml) · [英文源文件](en/vmware-vsphere.en.yaml)

### 14. Linux 服务器状态排行

按 CPU 使用率、可用内存、CPU I/O 等待及登录用户数分别排序，快速定位需要关注的 Linux 主机；最近问题组件显示当前用户有权限查看的所有主机问题。排行依赖 Linux 模板及 `target=linux` 标签，每项最多显示 10 台主机。

[简体中文源文件](zh-CN/linux-server-rankings.zh-CN.yaml) · [英文源文件](en/linux-server-rankings.en.yaml)

### 15. 基础设施问题与大屏

事件概览集中显示问题级别、当前问题及事件历史；运维大屏显示 Zabbix 系统信息、问题、Linux CPU 和可用内存排行。问题组件覆盖当前用户有权限查看的所有主机，Linux 排行依赖 `target=linux` 标签。可使用 Zabbix 全屏和幻灯片功能进行展示。

[简体中文源文件](zh-CN/infrastructure-operations.zh-CN.yaml) · [英文源文件](en/infrastructure-operations.en.yaml)

### 16. 交换机端口监控

选择 `target=generic` 的 SNMP 设备，查看自动发现端口的管理状态、运行状态、接收和发送速率及设备当前问题。各端口表最多显示 50 个监控项，按名称排序；可编辑组件调整上限或筛选上联端口。管理状态需要模板提供名称匹配 `Interface *: Administrative status` 的监控项；通用 SNMP 模板若未采集该项，该表会显示无数据，需要扩展发现规则或调整匹配名称。

[简体中文源文件](zh-CN/switch-port-status.zh-CN.yaml) · [英文源文件](en/switch-port-status.en.yaml)


### 17. 图形树交互浏览

参考 [Zabbix Graph Trees 模块](https://github.com/X-Mars/zabbix_modules/tree/master/zabbix_graphtrees)，通过主机组树选择主机，再在四个独立的监控项列表中各选一个数值型监控项，查看对应曲线。监控项按 `component` 标签值分组；未设置该标签的监控项位于“未分类”。图表使用仪表盘统一时间范围，默认每 10 秒刷新。无需安装模块或预先配置主机标签，数据受当前用户权限限制。

[简体中文源文件](zh-CN/graph-trees.zh-CN.yaml) · [英文源文件](en/graph-trees.en.yaml)

原生仪表盘与原模块存在差异：最多同时比较四个独立选择的监控项；标签筛选需在编辑各监控项导航组件时配置，不能在浏览时自由输入标签值；不具备模块的树搜索、跨图同步提示和单图全屏功能。列表也可能包含文本监控项，图表需选择数值型监控项。主机和监控项列表上限分别为 1000 和 500，可在组件设置中调整。

中英文版本均已在 Zabbix 8.0.0 测试环境导入。中文前端使用模拟 Linux 主机验证了主机切换、监控项列表联动、独立选择及曲线显示；测试数据为一次性写入。

## 专题仪表盘

以下六套使用 Zabbix 8.0 内置组件重新实现参考仪表盘，可与项目已有模板同时导入。组件布局、显示方式和筛选方式按 Zabbix 的能力适配，可能与其他平台的显示效果不同。

| 编号 | 对应功能 | 文件 |
| --- | --- | --- |
| 11209 | Linux 主机、性能曲线与 Zabbix 服务健康 | [中文](zh-CN/linux-server-overview.zh-CN.yaml) · [English](en/linux-server-overview.en.yaml) |
| 5456 | 服务器 CPU、内存、I/O、用户、文件系统及事件 | [中文](zh-CN/server-status-tables.zh-CN.yaml) · [English](en/server-status-tables.en.yaml) |
| 9711 | 交换机端口管理状态、运行状态与收发流量 | [中文](zh-CN/switch-ports-overview.zh-CN.yaml) · [English](en/switch-ports-overview.en.yaml) |
| 7171 | 问题严重性、当前问题及事件历史 | [中文](zh-CN/infrastructure-problems.zh-CN.yaml) · [English](en/infrastructure-problems.en.yaml) |
| 10797 | VMware 宿主机、数据存储和虚拟机 | [中文](zh-CN/vcenter-monitoring.zh-CN.yaml) · [English](en/vcenter-monitoring.en.yaml) |
| 5122 | 主机 CPU、内存、四条上联、环境、时钟和事件 | [中文](zh-CN/datacenter-tv.zh-CN.yaml) · [English](en/datacenter-tv.en.yaml) |

Linux、交换机及 VMware 分别使用 `target=linux`、`target=generic`、`target=vmware-hypervisor` / `target=vmware-guest` 标签。交换机管理状态要求监控项名匹配 `Interface *: Administrative status`。5122 的四条上联默认匹配所选设备的 `Interface *1/1*` 至 `Interface *1/4*` 收发监控项；温度和电池分别匹配 `*Temperature*` 和 `*UPS battery charge*`。实际设备名称不同时，请编辑组件中的监控项模式。5456 的文件系统表是多主机监控项表，不保证按空间使用率排序；问题组件显示有权限访问的全部主机。

复刻版已在开发说明指定的 Zabbix 8.0.0 环境导入 12 个语言版本。前端使用真实和模拟数据验证了多主机排序、文件系统、24 个端口、四条上联、环境指标、时钟、事件以及模拟 VMware 主机指标。模拟数据位于 `Dashboard Replica Test` 主机群组，名称以 `Replica TEST` 开头；另在已有模拟 ESXi 主机增加了数据存储总容量测试项。测试样本是一次性写入，不会持续更新，不代表真实设备状态。

## 验证情况

26 个语言版本共 38 个页面已在 Zabbix 8.0.0 完成前端数据验证。Linux、Zabbix 服务端、网络探测、网站、证书、数据库和容器使用实际采集数据。MySQL 使用 MariaDB 主从验证，Redis 使用兼容 Redis 协议的 Valkey 验证。Windows 和 VMware vSphere 使用明确标注的模拟目标验证。

新增 3 套的 6 个语言版本已在 Zabbix 8.0.0 测试环境通过 API 导入。中文页面验证了 Linux 实际数据、问题及已恢复事件、页面切换和 SNMP 测试目标的运行状态及流量。测试目标未提供端口管理状态，因此该项尚未进行有数据验证；服务器排行测试环境仅有一台匹配的 Linux 主机，未验证多主机排序。
