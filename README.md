# 修改二进制文件
更新自 [nishuoshenme/FGOFPSUnlocker](https://github.com/nishuoshenme/FGOFPSUnlocker)  
code中含有基于`日服2.24.1`制作的`libunity.so`文件, 解决宝具卡白屏问题  
## armeabi-v7a
使用`IDA Pro`打开`libunity.so`, 等待分析结束后按下`Shift + F12`打开字符串列表  
![open](https://github.com/tsuasahi/FGOFPSUnlocker/raw/master/imgs/1.png)  
按下`Ctrl + F`搜索  
```
set_targetFrame
```  
![search](https://github.com/tsuasahi/FGOFPSUnlocker/raw/master/imgs/2.png)  
得到结果  

![result](https://github.com/tsuasahi/FGOFPSUnlocker/raw/master/imgs/3.png)  
双击, 跳转到字符串  

![unk](https://github.com/tsuasahi/FGOFPSUnlocker/raw/master/imgs/4.png)  
等待上方字符串由`unk_2FCE40`变为`sub_2FCE40`后  

![sub](https://github.com/tsuasahi/FGOFPSUnlocker/raw/master/imgs/5.png)  
双击上方的函数`sub_2FCE40`, 跳转到如下位置  

![B](https://github.com/tsuasahi/FGOFPSUnlocker/raw/master/imgs/6.png)  
双击`B`右侧函数`sub_XXXXXX`继续跳转  

![code](https://github.com/tsuasahi/FGOFPSUnlocker/raw/master/imgs/7.png)  
跳转2到3次后应该能够看到代码  

![change](https://github.com/tsuasahi/FGOFPSUnlocker/raw/master/imgs/8.png)  
光标移至`00405A0C`行, 依次点击左上角`Edit->Patch program->Change byte`
  
然后把
  
```
04 10 9F E5 01 00 8F E7 1E FF 2F E1 D4 B5 9C 00
```
  
修改为
  
```
00 F0 20 E3 00 F0 20 E3 1E FF 2F E1 D4 B5 9C 00
```
  
![rate](https://github.com/tsuasahi/FGOFPSUnlocker/raw/master/imgs/9.png)  
之后双击上方`dword_DD0FEC`, 跳转后
  
点击`Edit->Patch program->Change byte`
  
然后把
  
```
FF FF FF FF 00 00 00 00 00 00 00 00 A0 36 CE 00
```
  
修改为你想设置的帧率, 比如60帧为
  
```
3C 00 00 00 00 00 00 00 00 00 00 00 A0 36 CE 00
```
  
90帧为
  
```
5A 00 00 00 00 00 00 00 00 00 00 00 A0 36 CE 00
```
  
120帧为
  
```
78 00 00 00 00 00 00 00 00 00 00 00 A0 36 CE 00
```
  
即前两位为十六进制帧数
  
最后, 点击`Edit->Patch program->Apply patches to input file...`并确定, 即可
  
## arm64-v8a
使用`ida pro`打开`libunity.so`, 等待分析结束后按下`Shift + F12`打开字符串列表  
![open](https://github.com/tsuasahi/FGOFPSUnlocker/raw/master/imgs/1.png)  
  
按下`Ctrl + F`搜索
```
set_targetFrame
```
  
![search](https://github.com/tsuasahi/FGOFPSUnlocker/raw/master/imgs/2.png)  
得到结果
  
![result64](https://github.com/tsuasahi/FGOFPSUnlocker/raw/master/imgs/10.png)  
双击, 跳转到字符串
  
![unity](https://github.com/tsuasahi/FGOFPSUnlocker/raw/master/imgs/11.png)  
等待上图出现后
  
![X](https://github.com/tsuasahi/FGOFPSUnlocker/raw/master/imgs/12.png)  
按`X`键查看引用, 双击第一个(如无第一个图示选项请等待)
  
![sub64](https://github.com/tsuasahi/FGOFPSUnlocker/raw/master/imgs/13.png)  
双击上方的函数`sub_30C400`, 跳转
  
![B64](https://github.com/tsuasahi/FGOFPSUnlocker/raw/master/imgs/14.png)  
然后点击2到3次`B`后面的函数`sub_XXXXXX`跳转到下图
  
![DWORD64](https://github.com/tsuasahi/FGOFPSUnlocker/raw/master/imgs/15.png)  
双击上方的函数`dword_F0FB5C`, 跳转后
  
![change](https://github.com/tsuasahi/FGOFPSUnlocker/raw/master/imgs/8.png)  
点击左上角`Edit->Patch program->Change byte`
  
然后把
  
```
FF FF FF FF 00 00 00 00 00 00 00 00 00 00 00 00
```
  
修改为你想设置的帧率, 比如60帧为
  
```
3C 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
```
  
90帧为
  
```
5A 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
```
  
120帧为
  
```
78 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
```
  
即前两位为十六进制帧数
  
![DWORD64](https://github.com/tsuasahi/FGOFPSUnlocker/raw/master/imgs/14.png)  
然后按`ESC`键, 回退到该段
  
光标移至`00400170`行, 依次点击左上角`Edit->Patch program->Change byte`
  
然后把
  
```
68 58 00 F0 00 5D 0B B9 C0 03 5F D6 C8 59 00 B0
```
  
修改为
  
```
1F 20 03 D5 1F 20 03 D5 C0 03 5F D6 C8 59 00 B0
```
  
最后, 点击`Edit->Patch program->Apply patches to input file...`并确定, 即可
  
***
  以上ᕕ( ᐛ )ᕗ
