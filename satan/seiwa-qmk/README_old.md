# 清和

> 注：此文档待整理，请勿参考。

## 核心设计哲学

简单来说，布局的设计原则为：在保持和标准布局差异尽量小的前提下，使手指的活动区域尽量小和自如，并均匀分摊左右手的压力。

### @LCtrl = '@CapsLock

很多程序猿，尤其是Emacs用户会做此设定，理由在于Caps Lock极少用到，而Ctrl的作用则重要得多。'@CapsLock一个很容易由左手小指按到的位置，并且不会限制其他手指的发挥，使LCtrl的组合键可以轻而易举地击打出来，比如：

1. LCtrl+C: `!L52`；LCtrl+X: `!L53`；LCtrl+Z: `!L54`。
1. Ctrl+Shift+T: `!L5R5L2`或`L5[@LShift]4[@LCtrl]2[T]`

这个设定使得LCtrl变得异常顺手，而RCtrl处在右下角最远的位置，几乎没有使用的机会。

### @CapsLock = [@Fn0][@Tab]

Caps Lock不论使用哪个按键都显得浪费（'@RCtrl似乎是个不错的选择？），使用组合键一点都不为过。这个组合键敲出来也毫不费力：`!L6[@LFn0]5[@Tab]`或`!L1[@LFn0](3|4)[@Tab]`

### @Fn0 = '@LCtrl

在60%键盘尤其是可编程键盘中，Fn的意义远远大于75%或标准大小的键盘，所有的功能键、Home、Delete之类特殊按键都需要使用Fn组合键来实现，因此，Fn也必须放置在一个易于击打的位置。

Emacs用户也大都听说过手掌按LCtrl的方法，相比LCtrl放在'@CapsLock而言，LCtrl+C, LCtrl+X之类的按键变得不那么方便，然而，用'@LCtrl作为Fn键实在是再合适不过了，因为Fn与哪些键能够组合完全是由我自己决定的。

### LFn与RFn

和Ctrl、Shift等一样，如果左手侧有被组合的按键，那么最好在右手侧设定一个Fn来分摊左手压力。

如果按照左右对称的原则来设计，那么@RFn0='@Menu，之所以没有这么做，一是因为它通常只用于与左手按键的组合，比如Up: [@RFn][@W]、Down: [@RFn][@S]，二是因为它右边还有RCtrl，使用`!R6`的时候易误触，三是当前的@RFn='@RFn，而使用`!R4[@RFn]`并不吃力。

### Esc

在60%键盘上，Esc一般被放在'@\`，这是个非常神奇的位置，对于Vim用户来说，Esc一下变得非常顺手：`!L(4|3)`即可。

而反引号（\`）并不常用，因此使用[@Fn][@Esc]变得自然而然。

另外，tkg.io中包含了Tricky Esc功能，使得输入`~`只需[@Shift][@Esc]，而不需要再使用Fn。

### 六个特殊键

Insert, Delete, Home, End, Page Up, Page Down

这几个特殊键我用得很少，除非我需要临时在Emacs以外的环境下工作，然而在剩余的按键中，这六个是最重要的了，因此我把它们按照相对位置不变的原则，将左上角的Insert安排在@J处，其他依次排开。

## 设计规范

### 层

* 修复了按住GUI (Win) 键强制KC_GESC发送`Grave` keycode的bug。

## 层

两个基本层：
0：Vim基本层
1: Emacs基本层

两个扩展层：
2: Vim扩展层
3: Emacs扩展层

一个控制层：
31: 控制层

#### 基本层

Vim基本层与标准GH60配列的差别如下：
1. `'@CapsLock`调整为`'@LCtrl`
1. `'@LCtrl`调整为`'@SWF`
1. `'@Fn`调整为`'@SWF`
1. `'@RWin`调整为`'@App`

Emacs基本层在Vim基本层上作如下调整：
1. `'@Esc`调整为`'@Tilde`

#### 扩展层

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
