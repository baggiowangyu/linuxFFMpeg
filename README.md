# linuxFFMpeg
linux下使用FFMPEG编程

###1.软件环境

操作系统环境：centos7

ffmpeg源码： [github上的master版本](https://github.com/FFmpeg/FFmpeg/tree/master "github上的master版本")（当前官网的3.4.1版本有bug，在主干中修复了'x264_bit_depth' undeclared）
x264源码：[x264-20180201版本](http://www.videolan.org/developers/x264.html)
SDL源码：[SDL1.2](http://www.libsdl.org/download-1.2.php)
Yasm源码：[yasm1.3.0](https://github.com/yasm/yasm)

###2.编译与安装

设置环境变量：（可以在/root/.bashrc脚本中设置，重启有效）

    export PATH="$PATH:/usr/local/bin:/usr/local/yasm/bin:/usr/local/SDL/bin:/usr/local/x264/bin"
    export PKG_CONFIG_PATH=/usr/local/lib/pkgconfig
    export C_INCLUDE_PATH="$C_INCLUDE_PATH:/usr/local/SDL/include/SDL:/usr/local/x264/include"
    export LD_LIBRARY_PATH="/usr/local/lib:/usr/local/SDL/lib:/usr/local/x264/lib:$LD_LIBRARY_PATH"

####2.1 yasm安装

    ./configure --prefix=/usr/local/yasm
    make
    make install

####2.2 SDL安装

    ./configure --prefix=/usr/local/SDL
    make
    make install

####2.3 x264安装

    ./configure --enable-shared --disable-asm --prefix=/usr/local/x264 
    make 
    make install

####2.4 ffmpeg安装

    ./configure --enable-shared --disable-static --enable-libx264 --enable-gpl --prefix=/usr/local/ffmpeg-master
    make
    make install

###3.安装好的库lib和头文件路径include

    /usr/local/yasm
    /usr/local/x264
    /usr/local/SDL
    /usr/local/ffmpeg-master

###4. 补充.几个解码库路径：

xvid  http://downloads.xvid.org/downloads/xvidcore-1.1.3.tar.gz 
mp3  http://lame.sourceforge.net/index.php 
Ogg  http://download.savannah.nongnu.org/releases/liboggpp/packages/
AC3  http://sourceforge.net/projects/ac3filter/ 
mpg4  http://sourceforge.net/projects/mpg/ 
3gp  http://www.3gpp.org/ftp/Specs 
VC1  http://neuron2.net/dgdecnv/dgdecnv.html
