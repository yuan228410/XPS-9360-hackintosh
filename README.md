# XPS-9360-hackintosh
hackintosh clover files for xps13-9360 with 8550U 
<br>

## 配置
Intel i7-8550U<br>
16GB RAM(SK Hynix)<br>
512GB ROM (samsung PM961)<br>
3200X1800 QHD Sharp<br>
DW1560 network card<br>
BIOS 2.8.1 <br>
MACOS 10.13.6<br>


## 安装步骤
1、安装之前使用DVMT.efi调整DVMT参数,见[the-darkvoid](https://github.com/the-darkvoid/XPS9360-macOS)<br>
2、high sierra已经支持多种NVMe固态，如果安装过程中识别不到PM961或其他固态，一般有两种原因：<br>
一是未开启archi(进BIOS修改即可)；<br>
二是固态牌子是海力士建兴浦科特，解决办法自行搜索。<br>
3、使用黑果小兵10.13.6镜像制作启动盘安装。<br>
4、安装过程中，第一次重启后，若安装过程中出现<br>
```
IOConsoleUsers: gIOScreenLockState 3, hs 0, bs 0, nov 0, sm 0x0
```
在clover界面的option的Graphic Injector中将injectIntel前面的对勾去掉。（其他问题详询我的个人网站）<br>
5、接下来就是安装到硬盘了，一般第一次安装到硬盘时会直接报错，这时候点击重新启动，再安装一次，这次会在安装结束时报错，不要紧，
直接将我的Clover文件拷贝到ESP分区的EFI文件夹下，设置好启动顺序，就可以顺利进入MAC系统了。<br>
6、接下来就是修改序列号、重建缓存以及修复屏幕等操作了这里不再赘述，其中注意的是，在今后的使用中，若开机时出现panic，
需要根据不同的报错，将对应的驱动从S/L/E中复制到Clover文件的/kexts/Others中，其他的不需要动，
[the-darkvoid](https://github.com/the-darkvoid/XPS9360-macOS)大神已经弄得很完美了。<br>
<br>

## 相对于the-darkvoid的文件的修改：
1、添加IE Capitan主题
2、删除ACPI/patched/SSDT-NVMe.aml
3、在config.plist添加
```
<key>Scan</key>
  <dict>
    <key>Entries</key>
    <true/>
    <key>Legacy</key>
    <false/>
    <key>Tool</key>
    <false/>
  </dict>
```
以隐藏多余启动项，需要显示按F3即可<br>
4、在KernelToPatch中添加相关代码去掉lilu输出信息以查看panic原因。
<br>

## 致谢
**[the-darkvoid](https://github.com/the-darkvoid/XPS9360-macOS)**<br>
**[rehabman](https://github.com/RehabMan/patch-nvme)**<br>
**[ymmshi](https://github.com/ymmshi/XPS-9360)**<br>
