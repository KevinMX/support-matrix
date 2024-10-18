---
sys: rtthread
sys_ver: null
sys_var: null

status: cft
last_update: 2024-10-18
---

# RT-Thread D1 Test Report

## Test Environment

### Operating System Information

- Download Link: https://github.com/RT-Thread/rt-thread/
- Reference Installation Document: https://github.com/RT-Thread/rt-thread/blob/master/bsp/allwinner/d1/README.md

### Hardware Information

- AWOL Nezha D1 / Sipeed Lichee RV Dock
- A microSD card
- A USB to UART Debugger (e.g., CH340, CH341, FT2232, etc.)

## Installation Steps

### Download Code

**Seems the methods in the Reference Installation Documen is unavaliable due to the toolchain link is changed.**

Download the RT-Thread code:
```bash
git clone https://github.com/RT-Thread/rt-thread.git
cd rt-thread/bsp/allwinner/d1
```

Get the toolchain:
```bash
git clone https://gitee.com/guozhanxin/rtthread-smart.git
cd rtthread-smart
python tools/get_toolchain.py riscv64
source smart-env.sh riscv64
```
If you can't automaticlly get the toolchain, you shall install riscv64-unknown-linux-musl toolchain and scons manually, and put riscv64-unknown-linux-musl under `tools/gnu_gcc/riscv64-linux-musleabi_for_x86_64-pc-linux-gnu/bin`.(Or you can read the `smart-env.sh` and change the PATH manually)

Configure the toolchain:
```bash
scons --menuconfig
source ~/.env/env.sh
pkgs --upgrade
```

Compile the kernel:
```bash
scons
```

### Flashing Image

Generate img:
Use the script `generateimg.sh` to generate image. You may need to install `u-boot-tools` first.
```bash
bash ./generateimg.sh
```

This image does not contain u-boot. You can use tftp to boot it. Put the img into your tftp server, and:
```bash
env edit serverip
# input your tftp server ip
dhcp
ping $serverip
tftp 8000000 rtthread.img
go 8000000
```

Or you can manually pack the u-boot into the image.

Use tina toolchain to pack the u-boot into image. You may need to get the tina toolchain on your own. See: https://club.rt-thread.org/ask/article/389ac36250b57737.html

### Logging into the System

Log into the system via the serial port.

## Expected Results

The system should boot up normally, allowing login through the onboard serial port.

## Actual Results

CFT

### Boot Log

Screen recording (from flashing the image to logging into the system):

```log
```

## Test Criteria

Successful: The actual result matches the expected result.

Failed: The actual result does not match the expected result.

## Test Conclusion

CFT
