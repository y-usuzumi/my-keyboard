# GH60(RevCHN)

一款使用了ATm32U4DFU微控制器的可编程键盘。

## 布局

[布局](layout.md)

### 如何编辑布局

1. 打开[https://tkg.io](https://tkg.io)，键盘菜单中选择`GH60 (RevCHN)`，层模式选择`标准`，并按需要设定层数。
1. 在[http://www.keyboard-layout-editor.com](http://www.keyboard-layout-editor.com)上进行各层的布局设定。每设定一层，就将Raw data标签页下的结果粘贴到步骤1页面相应的层中。
1. TKG页面中Fn节的内容会随着布局的定义自动变化，当所有的层设置完毕后，按需要设定每个Fn按钮的功能。
1. 最后在LED节设置背光。其中：“反向”表示当功能未激活时启用背光；背光表示是背光指示灯，否则是按键自身的指示灯。

## 如何刷写

两种方法：

1. （推荐）编辑完布局后直接在[https://tkg.io](https://tkg.io)页面上进行刷写：轻按键盘背后的复位按钮，稍等片刻后`烧写.eep文件`按钮会亮起。打开旁边的下拉菜单，确保引导程序选择`DFU`，固件选择`No Console`。点击`烧写.eep文件`按钮即可。
2. 使用`dfu-programmer`，暂不详述。
