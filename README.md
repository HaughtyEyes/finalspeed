# FinalSpeed [![Build Status](https://travis-ci.org/Bpazy/finalspeed.svg?branch=master)](https://travis-ci.org/Bpazy/finalspeed)
FinalSpeed是高速双边加速软件,可加速所有基于tcp协议的网络服务,在高丢包和高延迟环境下,仍可达到90%的物理带宽利用率,即使高峰时段也能轻松跑满带宽.

## Build
Java1.7 or higher is required. <br>
Windows: `winpcap`<br>
Linux: `libpcap`, `iptables`

### Windows
Build client: `gradlew releaseClient`<br>
Build server: `gradlew releaseServer`<br>
Build client&server: `gradlew release`

### Linux
Build client: `./gradlew releaseClient`<br>
Build server: `./gradlew releaseServer`<br>
Build client&server: `./gradlew release`

###Binary
Client: `output/FinalSpeedClient-version.jar`<br>
Server: `output/FinalSpeedServer-version.jar`<br>

`/output/libs/*.jar` is required.

## Usage
```
需要管理员权限
java -jar finalspeed.jar -b 运行CLI版
java -jar finalspeed.jar 运行GUI版
```

配置文件与finalspeed必须处在同一目录下.<br>
client_config.json
```
{
    // 下载速度，单位是 B，字节。这里换算起来就是 11MB。请把这里改成本机的下载速度
    "download_speed": 11200698, 
    // 协议：tcp 或 udp。注意：服务端如果是 OpenVZ 架构的话，则只支持 udp。
    "protocal": "udp", 
    // 服务器地址
    "server_address": "1.2.3.4", 
    // 一般不需要更改，保持默认即可。
    "server_port": 150, 
    // 不需要更改，保持默认即可。
    "socks5_port": 1083, 
    // 上传速度，单位是 B，字节。
    "upload_speed": 357469
}
```

port_map.json
```
{
    "map_list": [
        {
            // 要加速的服务器端口
            "dst_port": 12345, 
            // 本地端口
            "listen_port": 1099, 
            // 备注信息
            "name": "ss"
        }, 
        {
            "dst_port": 23456, 
            "listen_port": 2200, 
            "name": "ssh"
        }
    ]
}
```
