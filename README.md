<h1 align="center">喜马拉雅xm文件解密工具</h1>
<h4 align="center">Ximalaya-XM-Decrypt</h4>

### 说明

由于喜马拉雅官方客户端下载的音频文件为加密格式，无法在普通播放器中播放，所以我写了这个小工具来解密喜马拉雅下载的音频文件。本工具参考@aynakeya的[博文](https://www.aynakeya.com/2023/03/15/ctf/xi-ma-la-ya-xm-wen-jian-jie-mi-ni-xiang-fen-xi/)，并加入了批量解密的功能。我还写了一个程序[Ximalaya-Downloader](https://github.com/Diaoxiaozhang/Ximalaya-Downloader)，用于直接爬取未加密的喜马拉雅音频文件。本工具作为Ximalaya-Downloader的补充，当每日下载vip音频达到上限时，可以使用客户端下载加密的xm文件并使用本工具解密。

在使用该软件时，请确保xm_encryptor.wasm文件与主程序文件处在同一目录下，最好是一个单独的文件夹。

### 有缘人得见
#### 1.Ximalaya-Downloader已经无法正常使用了，期待能有大侠根据作者的源码进一步研究解决办法，目前只有采用手工下载.xm后用Ximalaya-XM-Decrypt来解密。
#### 2.解密失败的两种情况：
##### 2.1一种是下载文件不完整，表现为大小为0字节或者偏小，此时可以删除下载文件重新下载后再尝试解密。
##### 2.2一种是高清无损格式解码报错，如果你发现你下载的xm文件体积到了50-100M以上，就是flac格式了，此时解码报错。解决方法为：下载源码，注释掉main.py第156行即可解决。
#### 3.如果修改源码后仍然报错，请注意python的版本号，请注意python的版本号，请注意python的版本号，重要的事说三遍。
经本人实测，python 3.10正常，3.8和3.12都报错，主要原因为程序中用到的mutagen。
我看作者发布的0.13exe文件是python 3.9的，然而这货最新版本已移除对3.9的支持。说是支持3.10+,但是我的3.12报错后我就回滚到3.10了
项目地址：

https://github.com/quodlibet/mutagen

https://mutagen.readthedocs.io/en/latest/index.html

#### 4.好了就这么多，有缘人得见。
### 20260304
#### 为解决mpeg格式的音频文件转换而增加mpeg后缀
### 20260312
#### 为解决路径和文件名含特殊字符而修改replace_invalid_chars函数
#### 添加全角'｜'和 '：'转换
#### 将转换为" "改为转换为"_"，避免末尾出现空格而失败
