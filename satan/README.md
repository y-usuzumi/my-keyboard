# Satan a.k.a. GH60 RevCHN

一款使用了[ATmega32u4](http://www.microchip.com/wwwproducts/en/ATmega32u4)微控制器的可编程键盘，采用ANSI 60%布局。

### 固件

固件列表：

1. [清和 (seiwa)](seiwa-qmk/README.md)

## 刷写方法

目前所有的固件基于QMK。TMK已完全废弃。

以Arch Linux为例：

### 安装工具

```
$ sudo pacman -S avr-gcc avr-libc dfu-programmer dfu-utils
```

### 编译固件

```
$ git clone https://github.com/y-usuzumi/qmk_firmware.git
$ cd qmk_firmware
$ make gh60/satan:<固件代号>
```

固件代号即固件列表中括号内的部分，其他各部分参数具体含义请参照QMK文档：[https://docs.qmk.fm/](https://docs.qmk.fm/#/)。

> 老用户请注意：QMK近期更新导致make后的固件路径格式有变，欲知详情请直接执行`make`查看输出结果。

#### 刷写固件

可以使用dfu-programmer进行刷写，这里还是使用QMK官方推荐的方式：

```
$ sudo make gh60/satan:<固件代号>:dfu
```

注意！一定不要忘了`sudo`，否则将无法找到键盘。

执行后终端会不断刷新如下内容：

```
...
dfu-programmer: no device present.
ERROR: Bootloader not found. Trying again in 5s.
...
```

此时打开键盘的刷写开关（一般是位于底部的一个隐蔽的按钮），之后终端会输出刷写信息直到完成。键盘会自动重启。
