## Quickstart

### install

#### System environment dependence

operating system

- Linux
- Windows
- MacOS

java version: 1.8+

database server(default): MySQL/MariaDB

#### Database settings

Please see [Database setting](database.md)
            
#### Running the main program

    java -jar -Xms256m -Xmx1024G /opt/toughradius-latest.jar  --spring.profiles.active=prod
    
> Note the file (toughradius-latest.jar) path

#### Linux systemd config

> centos 7 example

write config files( see scripts dir)

    /etc/toughradius.env
    /usr/lib/systemd/system/toughradius.service

Run the following command

    systemctl enable toughradius
    systemctl start toughradius
    

