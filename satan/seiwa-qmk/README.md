# 清和Q

## 层

清和Q系列目前具有：

两个基本层：
0：Vim基本层
1: Emacs基本层

两个扩展层：
2: Vim扩展层
3: Emacs扩展层

一个控制层：
31: 控制层

### 基本层

Vim基本层与标准GH60配列的差别如下：
1. `'@CapsLock`调整为`'@LCtrl`
1. `'@LCtrl`调整为`'@SWF`
1. `'@Fn`调整为`'@SWF`
1. `'@RWin`调整为`'@App`

Emacs基本层在Vim基本层上作如下调整：
1. `'@Esc`调整为`'@Tilde`

### 扩展层

扩展层通过在基本层中按住Seiwa F键（下文简称SWF）激活，某些键的功能将会改变，下述为Vim扩展层的功能转换关系：
1. `'@Esc` -> `@Tilde`
1. `'@Bksp` -> `@Del`
1. `'@W` -> `@Up`
1. `'@S` -> `@Down`
1. `'@A` -> `@Left`
1. `'@D` -> `@Right`
1. `'@U` -> `@PrntScr`
1. `'@I` -> `@ScrLck`
1. `'@O` -> `@Pause`
1. `'@J` -> `@Ins`
1. `'@K` -> `@Home`
1. `'@L` -> `@PgUp`
1. `'@M` -> `@Del`
1. `'@Comma` -> `@End`
1. `'@Period` -> `@PgDn`
1. `'@Tab` -> `@CapsLock`
1. `'@1` -> `@F1` ... `'@0` -> `@F10`
1. `'@Minus` -> `@F11`
1. `'@Equal` -> `@F12`
1. `'@B` -> `@Backlight_Toggle`
1. `'@V` -> `@Backlight_Dec`
1. `'@N` -> `@Backlight_Inc`
1. `'@G` -> `@Audio_Play`
1. `'@F` -> `@Audio_Prev`
1. `'@H` -> `@Audio_Next`
1. `'@T` -> `@Audio_Stop`
1. `'@R` -> `@Audio_Rewind`
1. `'@Y` -> `@Audio_Forward`

Emacs扩展层在Vim扩展层的基础上作如下调整：
1. `@Tilde` -> `@Esc`

### 控制层

控制层用于在任意层中跳转（目前仅支持Vim与Emacs基础层的跳转，跳转至其他层引起故障后果自负）。

进入控制层的方法是：

`![@SWF][@SWF]Enter>>>`

（通俗描述：同时或先后按下两个SWF键，再按下Enter，再松开所有键）

此时，Q键切换基本层为0（Vim基本层），W键切换基本层为1（Emacs基本层）。若你想作死，可以尝试其他按键。

注意：这些修改会写入EEPROM，因此掉电不会丢失。

修改完毕按`'@Esc`退出控制层，此时会掉入你所设置的基本层。
