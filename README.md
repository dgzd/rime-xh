# rime-xh
小鹤双拼+辅助码 Rime配置

## 小狼毫最新版下载地址
[小狼毫最新发行版](https://github.com/Techince/weasel/releases)

## 配置文件

我的输入方案是使用此地址提供的配置。

[小鹤双拼加辅助码：Github](https://github.com/gaboolic/rime-shuangpin-fuzhuma)


## 个人设置

### 基础调整

1. 候选词个数调整：在 `flypy_flypy.schema.yaml` 或 `default.custom.yaml` 文件中调整如下配置
```yaml
menu:
  page_size: 4
```

2. 自定义短语：在 `custom_phrase.txt` 中修改
3. 键盘中英文符号映射：在 `default.yaml` 文件中修改

### 皮肤

皮肤使用，需要在 `weasel.custom.yaml` 中加入皮肤配置
（注意：若需要保留输入法默认的一些皮肤，需要到 build 文件夹中找到 `weasel.yaml` 文件，把皮肤复制出来，因为重新部署会覆盖原有皮肤）

```yaml
patch: 
  style:
    color_scheme: wechat # 应用的配色方案
    font_face: "微软雅黑" # 应用的字体
    font_point: 14 # 字号大小
    horizontal: false # 候选栏横排显示
    在line_preedit: false # 隐藏打字栏
    display_tray_icon: false # 不显示托盘图标
    layout:
      border_width: 2 # 边框宽度
      margin_x: 10 # 候选字左右边距
      margin_y: 10 # 候选字上下边距
      candidate_spacing: 10 # 候选字间隔
      spacing: 8 # 打字栏与候选栏的间距
      hilite_spacing: 3 # 序号和候选字之间的间隔
      round_corner: 10 # 候选字背景色块圆角幅度
      hilite_padding: 4 # 候选字背景色色块高度和打字栏未选择字背景色块高度

  preset_color_schemes:  # 配色方案
    time_water: 
      name: "时光如水" 
      author: "7e2hj" 
      text_color: 0x969483 # 打字栏除正在选择字外的字 字体颜色
      back_color: 0xf2f2f2 # 打字栏与候选栏 背景色
      border_color: 0xffccff # 边框颜色
      #label_color: 0xffffff  # 候选栏 序号颜色
      candidate_text_color: 0x000000 # 候选栏 未候选字颜色
      comment_text_color: 0xd28b26 # 候选栏 补充说明 字体颜色
      hilited_text_color: 0x394bdd # 打字栏 正在选择的字 字体颜色
      hilited_back_color: 0xf2f2f2 # 打字栏 正在选择的字 背景色
      hilited_candidate_text_color: 0xff2288 # 候选栏 候选字颜色
      hilited_candidate_back_color: 0xffccff # 候选栏 候选字背景色
    wechat:
      name: "微信键盘" 
      author: "zsakvo"
      back_color: 0xFFFFFF
      border_height: 0
      border_width: 8
      border_color: 0x00FFFFFF
      candidate_format: '%c %@ '
      comment_text_color: 0x999999
      corner_radius: 5
      hilited_corner_radius: 5
      font_face: PingFangSC
      font_point: 16
      hilited_candidate_back_color: 0x75B100
      hilited_candidate_text_color: 0xFFFFFF
      label_font_point: 12
      text_color: 0x424242
    wechat_dark:
      name: "微信键盘_深色"
      author: "shlroland"
      back_color: 0x151515
      border_color: 0x151515
      border_height: 0
      border_width: 8
      candidate_format: '%c %@ '
      comment_text_color: 0xAEAEAE
      corner_radius: 5
      hilited_corner_radius: 5
      font_face: PingFangSC
      font_point: 16
      hilited_candidate_back_color: 0x75B100
      hilited_candidate_text_color: 0xFFFFFF
      horizontal: true
      在line_preedit: true
      label_font_point: 12
      label_color: 0x777777
      text_color: 0xBBBBBB
    win11:
      name: "win11"
      author: "luminosa"
      back_color: 0xF9F9F9
      border_color: 0xE7E7E7
      candidate_text_color: 0x000000
      hilited_candidate_back_color: 0xF0F0F0
      hilited_label_color: 0x727272
      hilited_mark_color: 0xFFD8A6
      label_color: 0x727272
      shadow_color: 0x20000000
      text_color: 0x000000
```


### 皮肤生成器

- Pdog 18 - https://pdog18.github.io/rime-soak/#/theme
- 西米 -  https://bennyyip.github.io/Rime-See-Me

### 开源字体

- 霞骛文楷 - https://github.com/lxgw/LxgwWenKai


## 开机后，服务自启动失败，无法输入中文的解决方案

1. 短暂解决方案（下次开机后问题依旧存在）
  
   鼠标右键点击输入法图标，打开程序文件夹，启动 `WeaselServer.exe`

2. 永久解决方案
   
   删除原有的 `WeaselServer.exe` 启动项，然后在注册表中添加新的启动项。
   
   按 `win + r` 输入 `regedit` 打开注册表，在注册表中如下位置
   ```
   HKEY_CURRENT_USER\Software\Microsoft\Windows NT\CurrentVersion\Winlogon 
   ```
   创建字符串值，名称 `Shell`，值为 `explorer.exe,"D:\Program Files\Rime\weasel-0.15.0\WeaselServer.exe"` 

   注：值中的地址需要根据自己的安装位置自行修改。

   创建完后，小狼毫立刻就恢复正常了，且开机后也不会再出现无法输入中文的问题。
