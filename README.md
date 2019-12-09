# FFmpeg
FFmpeg编译源码及脚本，仅当编译记录

主要参考的编译流程及脚本来自：https://github.com/byhook/ffmpeg4android/blob/master/readme/android%E5%85%A8%E5%B9%B3%E5%8F%B0%E7%BC%96%E8%AF%91ffmpeg%E4%BB%A5%E5%8F%8Ax264%E4%B8%8Efdk-aac%E5%AE%9E%E8%B7%B5.md

### 编译环境：
Ubuntu:18.04    ndk版本:r12b    FFmpeg:3.4.7    fdk-aac:0.1.6

### 主要修改内容：  
1、修改config脚本的NDK路径，修改默认abi变量为THE_AECH=armv7a  
2、修改x264和fdk-aac编译脚本中的SYSROOT路径  
3、修改合并为单一库的脚本build_ffmpeg_with_fdk_x264_merge.sh的dynamic-linker路径，r12版本中libgcc.a的路径是4.9.x，增加rtsp分离器：--enable-demuxer=rtsp \  
4、fdk-aac最新版本为2.0.1，但修改了部分api会导致合并编译3.4.7版本的ffmpeg时不通过，所以用0.1.6版本  
5、还有遇到一个aac编译中找不到log.h的问题，找到该文件将#include "log/log.h"改为#include "android/log.h"  
