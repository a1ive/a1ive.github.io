---
layout: default
---

## Lua

### 加载 Lua 模块

​    `insmod lua`

### 进入 Lua 交互编程模式

​    在控制台中输入 `lua`

### 执行 Lua 脚本

​    `lua /path/to/script.lua`

### grub 函数库

- grub.run (`string` command)

  执行 GRUB 命令，若执行成功，则返回零，否则返回非零值。

- grub.script (`string` script)

  执行一行 GRUB 脚本，若脚本执行成功则返回零。

- grub.getenv (`string` variable)

  获取 GRUB 环境变量的值，若环境变量存在，则返回变量的值，否则，返回 `nil`。

- grub.setenv (`string` variable, `string` value)

  设置 GRUB 环境变量的值。第一个参数为变量名，第二个参数为变量内容。

- grub.exportenv (`string` variable[, `string` value])

  设置 GRUB 全局环境变量的值。第一个参数为变量名，第二个参数可选，为变量内容。

- grub.enum_device (`function` (`string` device[, `string` fs, `string` uuid, `string` label]))

  枚举 GRUB 的磁盘设备。

  参数为枚举执行的函数，可获取设备名，文件系统，UUID 和卷标。

- grub.enum_file (`function` (`string` filename))

  枚举某目录下的文件和文件夹 (包括 `.` 和 `..`)

- `userdata` file = grub.file_open (`string` filename[, `string` flag])

  打开文件，返回值为 `userdata` 类型的文件句柄。

  第一个参数是文件名。第二个参数为打开方式，若为 "w" 则以可写模式打开。

- grub.file_close (`userdata` file)

  关闭文件。

- grub.file_seek (`userdata` file, `integer` offset)

  设置文件句柄读写的位置偏移，返回值为偏移量。

- grub.file_read (`userdata` file, `integer` length)

  读取文件，长度为 "length"，返回文件内容。 

- grub.file_write (`userdata` file, `string` data)

  将字符串 "data" 写入文件。

- grub.file_getline (`userdata` file)

  从文件读取一行文本，返回值为该文本。

- grub.file_getsize (`userdata` file)

  返回文件大小。

- grub.file_getpos (`userdata` file)

  返回文件当前偏移量。

- grub.file_eof (`userdata` file)

  判断文件是否已读到末尾。

- grub.file_exist (`string` filename)

  判断文件是否存在。

- grub.file_crc32 (`string` filename)

  返回文件的 CRC32 校验值。

- `userdata` disk = grub.disk_open (`string` diskname)

  打开磁盘，返回值为 `userdata` 类型的磁盘句柄。

- grub.disk_close (`userdata` disk)

  关闭磁盘。

- `string` buf = grub.disk_read (`userdata` disk, `integer` sector, `integer` offset, `integer` length)

  读取磁盘指定扇区/偏移的数据，返回字符串。

- grub.disk_write (`userdata` disk, `integer` sector, `integer` offset, `integer` length, `string` buf)

  写入磁盘。

- `string` buf, `string` hex = grub.hexdump (`userdata` file, `integer` skip, `integer` length) 

  获取文件指定位置的十六进制数据。

- grub.add_menu

- grub.add_icon_menu

- grub.add_hidden_menu

- grub.clear_menu

- grub.read_byte

- grub.read_word

- grub.read_dword

- grub.write_byte

- grub.write_word

- grub.write_dword

- grub.cls

- grub.setcolorstate

- grub.refresh

- grub.read

- grub.gettext

- grub.get_time_ms

- grub.random

- grub.disk_getsize

### input 函数库

- input.getkey
- input.getkey_noblock
- input.read

### video 函数库

- video.swap_buffers
- video.fill_rect
- video.draw_string
- video.info

### gbk 函数库

- gbk.len
- gbk.byte
- gbk.char
- gbk.fromutf8
- gbk.toutf8