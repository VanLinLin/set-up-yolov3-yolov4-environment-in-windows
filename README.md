# 在 windows 10 內建立 darknet yolov3/yolov4 的環境(2021/08/11)

**軟體版本資源**

|軟體|版本|連結|
|:--:|:--:|:--:|
|CUDA|11.4|[CUDA](https://developer.nvidia.com/cuda-downloads?target_os=Windows&target_arch=x86_64&target_version=10&target_type=exe_network)|
|cuDNN|8.2.2|[cuDNN](https://developer.nvidia.com/rdp/cudnn-download#)|
|Visual Studio|2019|[Visual Studio](https://visualstudio.microsoft.com/zh-hans/vs/)|
|OpenCV|3.4.0|[OpenCV](https://opencv.org/releases/#)|
*** 

目錄
===============================================

*   [軟體安裝步驟](#download_step)

    *   [CUDA](#cuda)
        *   [CUDA 安裝步驟](#step)
    
    *   [cuDNN](#cudnn)
        *   [cuDNN 安裝步驟步驟](#step)
	
    *   [Visual Studio 2019](#visual_studio)
        *   [Visual Studio 2019 安裝步驟步驟](#step)
		
    *   [OpenCV](#opencv)
        *   [OpenCV 安裝步驟步驟](#step)


*   [顯示卡算力表](#power)

*** 

<h2 id="download_step">軟體安裝步驟</h2>


<h3 id="cuda">CUDA</h3>

1.進入CUDA下載連結，並依序選擇作業系統需求

P.S.選擇local或network皆可

![螢幕擷取畫面 2021-08-11 123339](https://user-images.githubusercontent.com/37219754/128970174-b8f5870f-b6e4-4028-ad51-b15c96ef6826.jpg)

2.點選下載

![螢幕擷取畫面 2021-08-11 123901](https://user-images.githubusercontent.com/37219754/128970624-666985c8-2c40-41fb-9404-48e2c06fd224.jpg)

3.下載完成後，啟動執行檔

![image](https://user-images.githubusercontent.com/37219754/128970856-dbc91bbf-8fb8-4723-9d54-50763c382130.png)

4.選擇下載路徑(可自訂)

![image](https://user-images.githubusercontent.com/37219754/129202066-e8420651-aaef-45d8-b9ad-2656bff9f1ea.png)


5.等待偵測相容性

![image](https://user-images.githubusercontent.com/37219754/129200801-8dbdae56-1027-4156-9cb2-eb5e3d59090d.png)

6.點選同意並繼續

![螢幕擷取畫面 2021-08-12 210025](https://user-images.githubusercontent.com/37219754/129201176-31bf37e3-1cd4-4e2e-968d-b0f73be56e63.jpg)

7.選擇快速即可，並點選下一步

![螢幕擷取畫面 2021-08-12 210025](https://user-images.githubusercontent.com/37219754/129201439-de83dfe4-091b-4773-9576-3499032be815.jpg)

8.等待安裝完成

![image](https://user-images.githubusercontent.com/37219754/129201536-13a366d7-148c-48e7-b88b-b1de84ccbfcc.png)

9.安裝結束後，打開cmd(命令提示字元)並輸入nvcc -V

![image](https://user-images.githubusercontent.com/37219754/129203176-70b94d7a-dc77-4683-aebf-bcf7cb685b96.png)

10.如有出現以下資訊，代表安裝成功(框內為版本號)

![螢幕擷取畫面 2021-08-12 210025](https://user-images.githubusercontent.com/37219754/129203084-7ec5f623-46a1-4875-999b-6b998542328f.jpg)


<h3 id="cudnn">cuDNN</h3>
