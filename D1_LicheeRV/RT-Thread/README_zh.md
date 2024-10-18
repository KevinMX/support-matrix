# RT-Thread Mangopi MQ 测试报告

## 测试环境

### 操作系统信息

- 下载链接：https://github.com/RT-Thread/rt-thread
- 参考安装文档：https://github.com/RT-Thread/rt-thread/blob/master/bsp/allwinner/d1/README.md

### 硬件信息

- AWOL Nezha D1 / Sipeed Lichee RV Dock
- microSD 卡一张
- USB to UART 调试器一个（如：CH340, CH341, FT2232 等）

## 安装步骤

### 下载代码

下载 RT-Thread 代码：
```bash
git clone https://github.com/RT-Thread/rt-thread.git
cd rt-thread/bsp/allwinner/d1
```

获取工具链：
```bash
git clone https://gitee.com/guozhanxin/rtthread-smart.git
cd rtthread-smart
python tools/get_toolchain.py riscv64
source smart-env.sh riscv64
```
资源可能已经失效？你可能需要自行下载一个riscv64-unknown-linux-musl工具链并安装scons，然后把工具链放到·tools/gnu_gcc/riscv64-linux-musleabi_for_x86_64-pc-linux-gnu/bin`（或者手动更改smart-env.sh中的路径）

配置工具链：
```bash
scons --menuconfig
source ~/.env/env.sh
pkgs --upgrade
```

编译内核：
```bash
scons
```

### 烧写镜像

生成img镜像：
使用`generateimg.sh`脚本来生成镜像。你可能需要安装`u-boot-tools`：
```bash
bash ./generateimg.sh
```

该系统镜像是不自带u-boot的，可以使用tftp的方式来启动。把镜像放到tftp服务器上然后：
```bash
env edit serverip
# input your tftp server ip
dhcp
ping $serverip
tftp 8000000 rtthread.img
go 8000000
```

或者你可以手动把u-boot打进去。这需要使用tina的工具链，获取后见论坛：https://club.rt-thread.org/ask/article/389ac36250b57737.html

### 登录系统

通过串口登录系统。

## 预期结果

系统正常启动，能够通过板载串口登录。

## 实际结果

CFT

### 启动信息


屏幕录像（从刷写镜像到登录系统）：

```log
```


## 测试判定标准

测试成功：实际结果与预期结果相符。

测试失败：实际结果与预期结果不符。

## 测试结论

CFT