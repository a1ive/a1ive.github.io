---
layout: default
---

## 主题

### 启用动态主题

```bash
export grub_frame_speed=110
```

其中，110为帧速，单位是毫秒每帧。

在 theme.txt 中使用动画容器

```scss
+ animation {
    dir_name = "IMAGE_DIR"
    image_format = png/jpg/jpeg/tga
    frame_number = n
    left = p%
    width = p%
    top = p%
    height = p%
    size_ratio = n
    start_x = n
    start_y = n
    move_speed = n
    move_direction = up/down/left/right
    play_once = pause/disappear
    hit_wall = pause/stop/disappear
    bind_menu = fixed_position/follow_single/foll_variety/full_screen
    bind_direction = left/right
}
```

### 属性说明

dirname = "IMAGE_DIR"

​    动画序列图片所在文件夹，指 theme.txt 所在目录下的文件夹

image_format = png/jpg/jpeg/tga

​    指定动画图片的扩展名，支持 png, jpg, jpeg, tga

frame_number = n

​    动画序列图片总数

​    图片文件命名必须是数字加扩展名，数字从 1 开始，例如 1.jpg, 2.jpg, 3.jpg ...

left/top/width/height = x/p%/p%+x

​    容器在屏幕中的左边距/上边距/宽度/高度

​    支持格式：百分比(p%), 像素(x), 百分比+像素(p%+x)

size_ratio = n

​    动画大小相对于容器的比例

start_x/start_y = n

​    动画在容器中x/y坐标的偏移值

​    若动画跟随主菜单选择条目的位置而移动，则 start_y 无效。

move_direction = up/down/left/right

​    设置动画初始的移动方向，只在随机移动的动画中有效

move_speed = n

​    设置动画移动速度

​    值为 0，则在原地播放动画。值不能为负数。

play_once = pause/disappear

​    设置动画播放一次后暂停显示最后一帧或消失

​    若不设置此项，则为循环播放。

hit_wall = pause/stop/disappear

​    设置当动画撞到容器壁后的行为

​    pause -- 暂停播放动画

​    stop -- 停止移动，继续播放动画

​    disappear -- 消失

bind_menu = fixed_position/follow_single/foll_variety/full_screen

​    设置动画作为随菜单选项变化的 logo 使用

​    若参数不是 follow_single，则动画序列应该放在 dir_name 参数目录的各子目录中，子目录名与 menuentry --class 的参数相同。

​    fixed_position -- 在固定位置随菜单项播放动画

​    follow_single -- 跟随菜单项，在不同位置显示同一组动画

​    follow_variety -- 跟随菜单项，在不同位置播放不同动画

​    full_screen -- 全屏显示随菜单项变化的动画

bind_direction = left/right

​    在启用跟随菜单项的动画后，设置动画的位置在主菜单左边框的左边或右边

### 菜单音效

设置变量 grub_sound_speed 以启用音效。单位是毫秒每音符

```bash
export grub_sound_speed=110
```

设置循环播放音效

```bash
export grub_sound_start="freq1 freq2 freq3 ..."
```

设置上下键选择菜单音效

```bash
export grub_sound_select="freq1 freq2 freq3 ..."
```

其中 freq1, freq2, freq3 ... 是频率，单位为赫兹

默认音效

```bash
grub_sound_start="220 277 330 440 185 220 277 370 294 370 440 587 330 415 494 659"
grub_sound_select="880 0 880 0 880 698 1046"
```
