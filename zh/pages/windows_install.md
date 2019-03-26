## Windows 安装运行

### java 运行环境

TOUGHRADIUS 依赖的 Java 版本最低为1.8，下载地址 [Java1.8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)


### 获得 TOUGHRADIUS 的编译文件 toughradius-latest.jar

- 可以自行通过Maven工具或Java Ide工具进行编译
- 从官方 QQ 群（247860313）获取最新编译好的jar文件


### 准备 MySQL 数据库环境

请参考 [数据库配置](database.md)

### 自定义配置文件

在运行目录下新建配置文件 application.properties, 根据实际情况自行修改配置，特别是数据库部分


    server.port = 1816
    server.security.require-ssl=true
    server.ssl.key-store-type=PKCS12
    server.ssl.key-store=classpath:toughradius.p12
    # The password used to generate the certificate
    server.ssl.key-store-password=toughstruct
    # The alias mapped to the certificate
    server.ssl.key-alias=toughradius

    server.http2.enabled=true
    server.address=0.0.0.0
    server.connection-timeout=600
    server.server-header=toughradius/1.0
    server.tomcat.accesslog.enabled=true
    server.tomcat.accesslog.directory=/var/log/toughradius
    spring.application.name=toughradius

    mybatis.config-locations=classpath:mybatis-config.xml
    mybatis.mapper-locations=classpath:mapper/*.xml

    # logging
    logging.config=classpath:logback-dev.xml
    logging.level.root=INFO
    logging.level.org.springframework.web=INFO

    # http
    spring.http.encoding.force=true
    spring.http.encoding.charset=UTF-8
    spring.http.encoding.enabled=true
    server.tomcat.uri-encoding=UTF-8
    spring.output.ansi.enabled=detect
    spring.jackson.time-zone=GMT+8
    spring.jackson.date-format=yyyy-MM-dd HH:mm:ss

    # component
    spring.cache.type=ehcache
    spring.cache.ehcache.config=classpath:/ehcache.xml

    #radius config
    org.toughradius.running=true
    org.toughradius.authport=${RADIUSD_AUTH_PORT:1812}
    org.toughradius.acctport=${RADIUSD_ACCT_PORT:1813}
    org.toughradius.rejectdelayEnabled=${RADIUSD_REJECT_DELAY_ENABLED:1}
    org.toughradius.rejectdelayTimes=${RADIUSD_REJECT_DELAY_TIMES:10}
    org.toughradius.rejectdelay=${RADIUSD_REJECT_DELAY:3}
    org.toughradius.trace=${RADIUSD_DEBUG:1}
    org.toughradius.authPool=${RADIUSD_AUTH_POOL:32}
    org.toughradius.acctPool=${RADIUSD_ACCT_POOL:32}
    org.toughradius.interimUpdate=120
    org.toughradius.maxSessionTimeout=86400
    org.toughradius.statDir=${RADIUSD_STAT_DIR:/var/toughradius/data/stat}
    org.toughradius.ticketDir=${RADIUSD_TICKET_DIR:/var/toughradius/data/ticket}
    org.toughradius.statfile=${RADIUSD_STAT_FILE:/var/toughradius/radiusd_stat.json}
    org.toughradius.isBillInput=true
    org.toughradius.isBillBackFlow=true
    org.toughradius.allowNegative=${RADIUSD_ALLOW_NAGATIVE:false}

    application.apikey = toughradius
    application.apisecret = toughradius
    application.version = v6.0.1

    logging.config=classpath:logback-prod.xml

    # database config
    spring.datasource.url=${RADIUS_RPCD_JDBC_URL:jdbc:mysql://127.0.0.1:3306/toughradius?serverTimezone=Asia/Shanghai&useUnicode=true&characterEncoding=utf-8&allowMultiQueries=true}
    spring.datasource.username=${RADIUS_RPCD_DBUSER:raduser}
    spring.datasource.password=${RADIUS_RPCD_DBPWD:radpwd}
    spring.datasource.max-active=${RADIUS_RPCD_DBPOOL:120}
    spring.datasource.driver-class-name=com.mysql.jdbc.Driver

### 运行

在运行目录下新建 startup.bat 文件，内容为

    java -jar -Xms256M -Xmx1024M toughradius-latest.jar

双击运行 startup.bat 即可


### 附注

如果熟悉 Springboot 程序部署的可以忽略以上说明