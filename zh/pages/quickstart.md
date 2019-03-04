## 快速开始

### 软件安装配置

#### 系统环境依赖

操作系统

- Linux
- Windows
- MacOS

jdk 版本: 1.8+

数据库服务器(默认): MySQL/MariaDB

#### 数据库配置

请参考 [数据库配置](database.md)
            
#### 运行主程序

    java -jar -Xms256m -Xmx1024G /opt/toughradius-latest.jar  --spring.profiles.active=prod
    
> 注意jar文件 (toughradius-latest.jar) 的路径

#### Linux 系统服务配置

> 以 centos 7 为例

配置文件 ( 见 scripts 目录)

    /etc/toughradius.env
    /usr/lib/systemd/system/toughradius.service

运行以下指令

    systemctl enable toughradius
    systemctl start toughradius
    

