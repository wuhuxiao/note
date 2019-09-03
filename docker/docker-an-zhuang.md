# Docker安装



### Windows 10安装docker

Windows 10 pro（专业版）可直接去docker官网安装 [Docker for Windows Installer.exe](https://download.docker.com/win/stable/Docker%20for%20Windows%20Installer.exe)

Windows 10 家庭版安装

1. 升级为专业版

   搜索专业版激活码，在电脑设置-关于电脑中升级

    ![](../.gitbook/assets/image%20%281%29.png) 

2. 安装[Docker for Windows Installer.exe](https://download.docker.com/win/stable/Docker%20for%20Windows%20Installer.exe)
3. 配置启动Hyper-V服务

   在电脑的服务配置中，启用服务

   ![](../.gitbook/assets/image%20%282%29.png) 

4. 使用cmd命令启动虚拟机服务

   pushd “%~dp0” dir /b %SystemRoot%\servicing\Packages_Hyper-V_.mum &gt;hyper-v.txt for /f %%i in \(‘findstr /i . hyper-v.txt 2^&gt;nul’\) do dism /online /norestart /add-package:"%SystemRoot%\servicing\Packages%%i" del hyper-v.txt Dism /online /enable-feature /featurename:Microsoft-Hyper-V-All /LimitAccess /ALL



   保存以上内容到txt文件，改文件名扩展为.cmd文件，以管理员身份运行此cmd文件即可

