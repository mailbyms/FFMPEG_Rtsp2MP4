# Rtsp2MP4
���� RTSP ��Ϊ mp4 �ļ�

## һ����Ŀ����

Visual Studio 2017

- �½�����̨��Ŀ

- ���� FFMPEG 64λ SDK (https://www.gyan.dev/ffmpeg/builds/packages/ffmpeg-4.3.2-full_build-shared.7z)������ѹ�� C �̸�Ŀ¼��

- �½�¼���� Recorder.h �� Recoder.cpp

- IDE ��� FFMPEG SDK:
	
	- ��Ŀ���ԣ��л��� Debug - x64
	  ```
	  C/C++
	      ����->����Ŀ¼������ ffmpeg �� include Ŀ¼������"C:\ffmpeg-4.3.2\include"
	  ������
        ����->���ӿ�Ŀ¼������ ffmpeg �� lib Ŀ¼������"C:\ffmpeg-4.3.2\lib"
    ����
        ������PATH=%PATH%;C:\ffmpeg-4.3.2\bin
    ```
    

## ����ʾ������

�ٷ���ʾ�����룺https://ffmpeg.org/doxygen/trunk/remuxing_8c-example.html

�޸�����

```
ɾ���� #include <libavutil/timestamp.h>

in_filename = "rtsp://192.168.0.49/24.mp4";
out_filename = "camera_1.mp4";
	
stream_mapping = (int *)av_malloc(stream_mapping_size * sizeof(*stream_mapping));

while(1) ѭ��������������������ִ�к���� av_write_trailer
```



ע�⣺

- һ��Ҫִ�� av_write_trailer������ mp4 �ļ����ܲ���

- AVStream::codec  ������Ϊ�ѷ��
  ffmpeg 3.3 ��ʼ���°汾AVStream�ķ�װ��������codec�滻codecpar���� avcodec-58 ��ʼ����������д����ʱ��IDE��ʾ��***�����ѱ�����������

  ```
  1. ��Ŀ����  C/C++ > ���� -> SDL checks�ص�
  2. ��������ӱ��������Ϣ  #pragma warning(disable: 4996) 
  ```

