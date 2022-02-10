# Rtsp2MP4
保存 RTSP 流为 mp4 文件

## 一、项目建立

Visual Studio 2017

- 新建控制台项目

- 下载 FFMPEG 64位 SDK (https://www.gyan.dev/ffmpeg/builds/packages/ffmpeg-4.3.2-full_build-shared.7z)，并解压到 C 盘根目录下

- 新建录制类 Recorder.h 和 Recoder.cpp

- IDE 添加 FFMPEG SDK:
	
	- 项目属性，切换到 Debug - x64
	  ```
	  C/C++
	      常规->附加目录：增加 ffmpeg 的 include 目录，例如"C:\ffmpeg-4.3.2\include"
	  链接器
        常规->附加库目录：增加 ffmpeg 的 lib 目录，例如"C:\ffmpeg-4.3.2\lib"
    调试
        环境：PATH=%PATH%;C:\ffmpeg-4.3.2\bin
    ```
    

## 二、示例代码

官方的示例代码：https://ffmpeg.org/doxygen/trunk/remuxing_8c-example.html

修改内容

```
删掉了 #include <libavutil/timestamp.h>

in_filename = "rtsp://192.168.0.49/24.mp4";
out_filename = "camera_1.mp4";
	
stream_mapping = (int *)av_malloc(stream_mapping_size * sizeof(*stream_mapping));

while(1) 循环增加了跳出条件，以执行后面的 av_write_trailer
```



注意：

- 一定要执行 av_write_trailer，否则 mp4 文件不能播放

- AVStream::codec  被声明为已否决
  ffmpeg 3.3 开始，新版本AVStream的封装流参数由codec替换codecpar，即 avcodec-58 开始。如果在运行代码的时候，IDE提示，***声明已被否决，解决：

  ```
  1. 项目属性  C/C++ > 常规 -> SDL checks关掉
  2. 代码中添加编译参数信息  #pragma warning(disable: 4996) 
  ```

