# 在 windows 10 內建立 darknet yolov3/yolov4 的環境(2021/08/11)

**軟體版本資源**

|軟體|版本|連結|
|:--:|:--:|:--:|
|CUDA|11.4|[CUDA](https://developer.nvidia.com/cuda-downloads?target_os=Windows&target_arch=x86_64&target_version=10&target_type=exe_network)|
|cuDNN|8.2.2|[cuDNN](https://developer.nvidia.com/rdp/cudnn-download#)|
|Visual Studio|2019|[Visual Studio](https://visualstudio.microsoft.com/zh-hans/vs/)|
|OpenCV|3.4.0|[OpenCV](https://opencv.org/releases/#)|
|darknet|---|[darknet](https://github.com/AlexeyAB/darknet)|
*** 

目錄
===============================================

*   [軟體安裝步驟](#download_step)

    *   [CUDA](#cuda)
        *   [CUDA 安裝步驟]
    
    *   [cuDNN](#cudnn)
        *   [cuDNN 安裝步驟]
	
    *   [Visual Studio 2019](#visual_studio)
        *   [Visual Studio 2019 安裝步驟]
		
    *   [OpenCV](#opencv)
        *   [OpenCV 安裝步驟](#download)
        *   [環境變數設置步驟](#change_environment_variable)

    *   [darknet](#darknet)
        *   [darknet 安裝步驟](#darknet_set_up)



        *   [CUDA 版本修改](#version)
            *   [darknet.vcxproj](#darknet_vcproj_cuda)
            *   [yolo_cpp_dll.vcxproj](#yolo_cpp_dll_cuda)



        *   [顯卡算力修改](#change_power)
            *   [取得算力](#get_power)
            *   [darknet.vcxproj](#darknet_vcproj_power)
            *   [yolo_cpp_dll.vcxproj](#yolo_cpp_dll_power)   

*   [編譯步驟](#compile)

    *   [darknet.sln](#darknet_sln)
        *   [介紹]
        *   [步驟]
    
    *   [yolo_cpp_dll.sln](#yolo_cpp_dll)
        *   [介紹]
        *   [步驟]

*   [顯示卡算力表](https://developer.nvidia.com/cuda-gpus)

*** 

<h2 id="download_step">軟體安裝步驟</h2>


<h3 id="cuda">。CUDA</h3>

***

1.進入CUDA下載連結，並依序選擇作業系統需求

P.S.選擇local或network皆可

![螢幕擷取畫面 2021-08-11 123339](https://user-images.githubusercontent.com/37219754/128970174-b8f5870f-b6e4-4028-ad51-b15c96ef6826.jpg)

2.點選下載

![螢幕擷取畫面 2021-08-11 123901](https://user-images.githubusercontent.com/37219754/128970624-666985c8-2c40-41fb-9404-48e2c06fd224.jpg)

3.下載完成後，啟動執行檔

![image](https://user-images.githubusercontent.com/37219754/128970856-dbc91bbf-8fb8-4723-9d54-50763c382130.png)

4.選擇下載路徑(雖然可以選，但是安裝完成後似乎都會改到C碟)

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


<h3 id="cudnn">。cuDNN</h3>

***

1.進入cuDNN官方網站，並登入(若沒有帳號需先辦一個，並填寫一份問卷)

![image](https://user-images.githubusercontent.com/37219754/129222195-dd217dde-0b08-49e4-bb95-a70270de6f2b.png)

2.勾選同意協議後，選擇對應到CUDA版本(11.4)的cuDNN(8.2.2)

![129204716-60825914-8dca-400f-bd4d-748428ab4e17](https://user-images.githubusercontent.com/37219754/129222567-100beeab-c01a-403d-aee6-dd1f8915045d.png)

3.選擇windows(x86)並開始下載(路徑為D:\cudnn)

![螢幕擷取畫面 2021-08-12 210025](https://user-images.githubusercontent.com/37219754/129222619-984600fd-f9e7-439f-a28f-d95634449b72.jpg)

4.下載完成後，會有一個zip壓縮檔

![image](https://user-images.githubusercontent.com/37219754/129222938-adb3c8fb-8f90-4f9a-bc76-3318a0bc38db.png)

5.解壓縮後，會有一份cuda資料夾，裡面還會有3份資料夾(bin，include，lib)與一份txt文字檔(NVIDIA_SLA_cuDNN_Support.txt)，分別與剛剛下載的CUDA資料夾相對應

。cuDNN資料夾

![image](https://user-images.githubusercontent.com/37219754/129223218-fcc9fc67-2421-4843-a58a-4fc34a50cd92.png)

。CUDA資料夾(路徑已更改為C碟)

![螢幕擷取畫面 2021-08-12 232411](https://user-images.githubusercontent.com/37219754/129223938-0a9c79d2-853c-492b-9859-bfec84c50c43.jpg)

6.將cuDNN的3份資料夾內的資料複製到CUDA相對應的資料夾內

。bin

![bin](https://user-images.githubusercontent.com/37219754/129225295-a4664a25-3441-4575-97f6-1d021e968581.jpg)

。include

![include](https://user-images.githubusercontent.com/37219754/129225339-6e4b0abd-e5fe-4844-8074-bfbe3f1b00fc.jpg)

。lib(需進入到x64檔案夾內)

![lib](https://user-images.githubusercontent.com/37219754/129225414-cffa8166-61a0-444b-954c-99ac9e468f49.jpg)


<h3 id="visual_studio">。Visual Studio 2019</h3>

***

1.進入連結後，選擇community 2019，會自動開始下載的動作

![螢幕擷取畫面 2021-08-12 234727](https://user-images.githubusercontent.com/37219754/129227533-bc1fcaee-9a1e-4d98-a78f-2c4e0e98727b.jpg)

2.下載完成後，會得到一個執行檔

![image](https://user-images.githubusercontent.com/37219754/129227856-9e65f97c-3a27-4d9c-bb51-d3e9a06f76b0.png)

3.啟動執行檔，並勾選需要的模塊(左下角可以選擇下載位置)

![image](https://user-images.githubusercontent.com/37219754/129228291-9cb4c189-2ad9-4a78-a486-167a4d2e5e73.png)

![image](https://user-images.githubusercontent.com/37219754/129228451-1e6fd30b-a07a-4d49-8b71-2960efb20fcd.png)


<h3 id="opencv">。OpenCV</h3>

***

<h4 id="download">。OpenCV 安裝步驟</h4>

1.進入連結後，找到 opencv3.4.0 for windows 並下載(可選擇路徑)

![螢幕擷取畫面 2021-08-12 235655](https://user-images.githubusercontent.com/37219754/129229105-1b7bf2c5-2691-479c-b783-7a04056f3539.jpg)

2.下載完成後，會有一個opencv資料夾

![image](https://user-images.githubusercontent.com/37219754/129229974-9240dd07-ee56-4074-b0f9-3d775972c772.png)

<h4 id="change_environment_variable">。環境變數設置步驟</h4>

1.搜尋環境變數並開啟

![螢幕擷取畫面 2021-08-13 000914](https://user-images.githubusercontent.com/37219754/129230704-b1be9934-ef99-4640-9f83-9fb85a99c134.jpg)

2.開啟後，點選環境變數(N)

![螢幕擷取畫面 2021-08-13 001022](https://user-images.githubusercontent.com/37219754/129230861-9a78063d-1f8e-4a62-8ab2-1ad6d1532786.jpg)

3.選擇新增(N)

![螢幕擷取畫面 2021-08-13 001213](https://user-images.githubusercontent.com/37219754/129231139-91a7cfdb-420c-484e-98ea-ad14fb20bb13.jpg)

4.將opencv檔案內的opencv以及opencv2目錄新增進去(可使用瀏覽目錄選擇)，完成後選擇確定

。opencv

![image](https://user-images.githubusercontent.com/37219754/129231431-735a68ed-cfcc-449c-8ec8-b5a35f4b2191.png)

。opencv2

![image](https://user-images.githubusercontent.com/37219754/129231584-6f414240-af20-413c-bcf3-798a71361b50.png)

。完成狀態

![螢幕擷取畫面 2021-08-13 001643](https://user-images.githubusercontent.com/37219754/129231766-87b2b462-4e8f-4d85-85b7-cb68dd2f3605.jpg)


<h3 id="darknet">。darknet</h3>

***

<h4 id="darknet_set_up">。darknet 安裝步驟</h4>

1.進入網址後，選擇code -> download ZIP，並將檔案下載至自訂路徑

![螢幕擷取畫面 2021-08-13 002217](https://user-images.githubusercontent.com/37219754/129232587-99ea8be6-635f-4a6e-97db-27494e1edfe0.jpg)

2.下載完成後，會得到一個zip壓縮檔

![image](https://user-images.githubusercontent.com/37219754/129233011-0a2474ce-d700-49c7-9355-8c2246950a2f.png)

3.解壓縮後，會得到一份darknet-master資料夾

![image](https://user-images.githubusercontent.com/37219754/129233130-36681651-a4a4-4b5b-a54f-43838ae79cce.png)

<h4 id="version">。CUDA 版本修改</h4>

<h5 id="darknet_vcproj_cuda">。darknet.vcxproj</h5>

1.進入darknet路徑(darknet-master\build\darknet)，找到darknet.vcxproj並用筆記本打開(NotePad++ 或其他)

![螢幕擷取畫面 2021-08-13 003237](https://user-images.githubusercontent.com/37219754/129234028-54434e3f-7ad5-48ee-b446-905006e43245.jpg)

2.ctrl + f 開啟搜尋模式並搜尋CUDA

![image](https://user-images.githubusercontent.com/37219754/129234521-50852bfb-e832-4ebe-b4e3-b8f98aaa5943.png)

3.找到原始CUDA版本並將版本更新為下載的版本11.4(總共有2處)

。1

![螢幕擷取畫面 2021-08-13 004146](https://user-images.githubusercontent.com/37219754/129235294-25725150-959d-44a5-8fcb-f121daa157f7.jpg)


。2

![螢幕擷取畫面 2021-08-13 004015](https://user-images.githubusercontent.com/37219754/129235155-f7481c28-2cb0-43c5-bbc7-5b011ef267fd.jpg)


<h5 id="yolo_cpp_dll_cuda">。yolo_cpp_dll.vcxproj</h5>

1.進入darknet路徑(darknet-master\build\darknet)，找到yolo_cpp_dll.vcxproj並用筆記本打開(NotePad++ 或其他)

![螢幕擷取畫面 2021-08-13 011218](https://user-images.githubusercontent.com/37219754/129239580-03cb18f7-99fe-4a88-8c52-5f77d806ae13.jpg)

2.ctrl + f 開啟搜尋模式並搜尋CUDA，然後更新為新版本11.4(總共有2處)

。1

![螢幕擷取畫面 2021-08-13 011522](https://user-images.githubusercontent.com/37219754/129239901-7a0a8bb4-e353-4296-9b98-18d6f704062d.jpg)

。2

![螢幕擷取畫面 2021-08-13 011758](https://user-images.githubusercontent.com/37219754/129240246-3035cf1c-5318-40d0-9b31-5dd697c4243d.jpg)


<h4 id="change_power">。顯卡算力修改</h4>

<h5 id="get_power">。取得算力</h5>

1.搜尋Nvidia Control Panel

![image](https://user-images.githubusercontent.com/37219754/129236115-190482e3-09fb-4f56-8e3c-57a77a224e30.png)

2.找到自己的型號，並參考[顯示卡算力表](https://developer.nvidia.com/cuda-gpus)取得顯卡的算力

![螢幕擷取畫面 2021-08-13 004840](https://user-images.githubusercontent.com/37219754/129236309-25a309cd-e726-428c-9ded-6ecf1ec45dd2.jpg)

3.進入自己的顯卡名單

![螢幕擷取畫面 2021-08-13 005557](https://user-images.githubusercontent.com/37219754/129237411-350c50b2-8213-4617-b317-c36ae3d3fd02.jpg)

4.取得顯卡算力(須乘以10)，e.g. 6.1 x 10 = 61

![螢幕擷取畫面 2021-08-13 005832](https://user-images.githubusercontent.com/37219754/129237639-88775c3e-9260-493a-808c-00a3ed36667d.jpg)


<h5 id="darknet_vcproj_power">。darknet.vcxproj</h5>

1.進入darknet.vcxproj，並搜尋compute

![image](https://user-images.githubusercontent.com/37219754/129240770-9438ea44-19bc-4a14-a7cb-3a1db7948dc6.png)

2.將compute_30,sm_30;compute_75,sm_75修改為compute_61(依照自己的顯卡算力)(總共有2處)

。1

![螢幕擷取畫面 2021-08-13 012457](https://user-images.githubusercontent.com/37219754/129241224-121280ce-715d-4046-bf76-ad7f1275acd9.jpg)

。2

![螢幕擷取畫面 2021-08-13 012441](https://user-images.githubusercontent.com/37219754/129241357-ad3a5086-c614-4239-9c8e-fbf917a708dc.jpg)


<h5 id="yolo_cpp_dll_power">。yolo_cpp_dll.vcxproj</h5>

1.進入yolo_cpp_dll.vcxproj，搜尋compute後，修改算力(一樣有2處)

。1

![螢幕擷取畫面 2021-08-13 012457](https://user-images.githubusercontent.com/37219754/129241843-ff8479f3-d80d-4205-948c-7dde1b60a04a.jpg)

。2

![螢幕擷取畫面 2021-08-13 012857](https://user-images.githubusercontent.com/37219754/129241947-5c6bd928-2a91-412a-8ce9-e8812968fc10.jpg)




