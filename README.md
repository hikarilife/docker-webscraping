# docker-webscraping
jupyterlab and selenium with chrome debug on docker
  
# How to use
## Step1
ファイルをローカルにダウンロードします。  
The mirror of the docker-rvm can be checked out with the following command:
```
git clone https://github.com/hikarilife/docker-rvm.git
```
  
## Step2
ビルドして動かします。  
Build and run docker-webscraping container with the following command:
```
docker-comopse up -d --build
```
  
## Step3
操作するchromeの様子を確認するためにVNC接続します。  
Connect to the VNC by VNC connector like VNC Viewer for debu chrome with following ip addresss and port number:
```
localhost:5900
```
  
## Step4
JupyterLabを開きます。  
Open the JupyterLab by web browser on localhost with following url:
```
http://localhost:8888
```
  
## Step5
JupyterLabで下記を実行して、ちゃんと動作するか確認します。  
Check the containers is working with following script on JupyterLab:
```
from selenium import webdriver
from selenium.webdriver.common.desired_capabilities import DesiredCapabilities
browser = webdriver.Remote(
  command_executor='http://<container-name>:4444/wd/hub',
  desired_capabilities=DesiredCapabilities.CHROME)
browser.get('https://github.com/hikarilife/docker-webscraping')
```
