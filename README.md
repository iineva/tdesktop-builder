# 网盘地址（欢迎上传到别的网盘的朋友追加一下）

百度网盘：https://pan.baidu.com/s/1E19Ykmrkm29VDzMqEwH-kw 提取码：v3hi

# 文件MD5

* MD5 (TBuild.rar) = 5340d240306f0eaff9aa920f702d9be4
* MD5 (python-2.7.17.amd64.msi) = 55040ce1c1ab34c32e71efe9533656b8
* MD5 (vs_community_2017_1889860080.1578036349.exe) = 1dea05839475e38d9ba7e346b4142797

# 相关链接

https://github.com/telegramdesktop/tdesktop/blob/dc8abc74ed4d72a73315550b91283ff1f2e44199/docs/building-msvc.md
https://github.com/nebula-chat/chatengine
https://github.com/nebula-chat/clients/tree/master/tdesktop

# 文件说明

* 所有依赖库已编译好，编译环境是 Windows 10 Pro + VS 2017，系统设置成了英文完成了编译
* 本包中的文件是从成功编译的虚拟机中精简提取出来打包而成
* 本包中的文件已放进重新安装的干净的虚拟机 Win 10 Pro（系统语言中文）中按照下面描述的步骤成功进行编译

# 代码说明

* tdesktop 代码用的是 `dc8abc74ed4d72a73315550b91283ff1f2e44199`
* 基于打了这个补丁，另外修复了补丁编译问题：https://github.com/nebula-chat/clients/tree/master/tdesktop
* 更换了默认聊天背景图
* 另外有两个文件因为编译问题修改了存储字符编码，代码未做任何改动， `ffmpeg\libavutil\rational.h` `Telegram\SourceFiles\ui\text\text.cpp`
* tdesktop目录是clone官方仓库，可将该目录导入到git图形客户端查看具体改动，推荐使用 `Github Desktop` 可直接预览图片改动

# 环境配置

* 修改系统环境变量`PATH`添加两个值：`C:\TBuild\ThirdParty\gyp` `C:\TBuild\ThirdParty\Ninja`
* 安装Python27：打开 `python-2.7.17.amd64.msi` ，安装时设置安装目录：`C:\TBuild\ThirdParty\Python27\`
* 安装VS2017：打开 `vs_community_2017_1889860080.1578036349.exe` ，安装时勾选 `通用Windows平台开发` 或者 `使用C++的桌面开发`，推荐选择后者不用下载这么多数据

# 编译方法

* 解压 `TBuild.rar` 到 `C:\`
* 将`Telegram\SourceFiles\config.h`中的`NEBULAIM_DC_IP4`对应的值替换成自己的服务器IP
* 打开项目 `C:\TBuild\tdesktop\Telegram\Telegram.sln` 鼠标定位到 `Telegram` 右键 `Build`
* 输出目标在`C:\TBuild\tdesktop\out\(Debug|Release)`中

# 出错处理

如果编译过程中提示某文件编码需要转 Unicode 使用 `Sublime Text` 将文件重新保存成 `UTF-8 with BOM` 编码即可重新编译，注意选择编码后需要在文件中随意输入一个字符再删除，才能成功修改编码保存

由于包比较大，压缩时间比较长，就麻烦自己手动操作处理一下了，已知文件：
`TBuild\tdesktop\Telegram\ThirdParty\libtgvoip\VoIPController.cpp`
