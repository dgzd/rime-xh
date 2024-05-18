# rime-xh
小鹤双拼+辅助码 Rime配置

## 小狼毫下载地址
[官方Github](https://github.com/rime/weasel/releases)

## 配置文件

我的输入方案是使用此地址提供的配置。

[小鹤双拼句中任意字后加辅助码：Github](https://github.com/gaboolic/rime-shuangpin-fuzhuma)


## 个人设置

### 基础调整

1. 候选词个数调整：新增 `flypy_flypy.custom.yaml` 文件，在其中修改
```yaml
patch:
  menu/page_size: 4
```

2. 自定义短语：在 `custom_phrase.txt` 中修改
3. 键盘中英文符号映射：可以把需要修改的符号对抽取到 `flypy_flypy.custom.yaml` 文件中。符号对参照参照`default.yaml`

### 皮肤

在 `weasel.custom.yaml` 中修改皮肤配置，若有需要，可下载我在此仓库中提供的文件

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


## 安卓端小企鹅输入法配置教程

### 小企鹅输入法下载

1. 打开[官方下载地址：fcitx-android](https://jenkins.fcitx-im.org/job/android/)
2. 至少下载主程序和 rime 插件

- fcitx5-android：小企鹅输入法主程序
- fcitx5-android-plugin-rime：适用于小企鹅输入法的rime插件
- fcitx5-android-updater：小企鹅输入法更新器

### 配置
1. 安装输入法主程序，再安装 rime 插件
2. 在手机系统设置中启用并切换到小企鹅输入法
3. 在输入法中添加**中州韵**
4. 把配置文件放入下列文件夹中
   ```
   /Android/data/org.fcitx.fcitx5.android/files/data/rime/
   ```
5. 退出输入法后重新打开   
