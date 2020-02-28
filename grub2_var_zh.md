---
layout: default
---

## 变量

| 变量名称               | 默认值  | 含义                                |
| ---------------------- | ------- | ----------------------------------- |
| grub_prompt            | grub>   | GRUB 命令提示符                     |
| grub_disable_esc       | 0       | 0为允许使用 ESC 热键返回上一级菜单  |
| grub_cmdline           | <unset> | 从上一级 EFI 启动器接收到的命令行   |
| grub_fs_case_sensitive | <unset> | 值为1,则支持大小写敏感文件名        |
| grub_draw_border       | <unset> | 值为1，则绘制菜单边框               |
| grub_frame_speed       | <unset> | 动画主题帧速，单位为毫秒/帧         |
| grub_sound_speed       | <unset> | 蜂鸣器声音播放速度，单位为毫秒/音符 |
| grub_sound_start       | <unset> | 自定义循环播放音乐                  |
| grub_sound_select      | <unset> | 自定义上下键选择菜单音效            |
