# ![](https://th.bing.com/th?id=ODLS.194d04fb-feff-41d9-b83c-1cbe98afa6ec&w=32&h=32&o=6&pid=13.1) **<font color=""> Magento Training Exercises</font>**

>### **<font color="#4267b2"> Chapter # 1 Exercises</font>**

##### Exercises # 1.1<font color="Yellow"> ( Created an empty Hello World module in app/code & enable it) </font>

###### **<font color="Green">Answer</font>** In this exercise, created an empty module `HelloWorld` and anable it & use these commands

- <small>Enable `Unit1_HelloWorld` module</small>
```shell
sudo php bin/magento module:enable Unit1_HelloWorld
```
- <small>Setup Upgrade</small>
```shell
sudo php bin/magento setup:upgrade
```
- <small>Give Permissions</small>
```shell
sudo chmod -R 777 var/ pub/ generated/ app/etc/
```
<details>
    <summary markdown="span">Picture of module <code>HelloWorld</code></summary>
    <image src="https://data.terabox.com/thumbnail/426b09581922013ac65e8e66f3aea508?fid=4400792537950-250528-275316974625091&time=1686294000&rt=sh&sign=FDTAER-DCb740ccc5511e5e8fedcff06b081203-fXrwRoAyp7VYULUEvgnBe9qxObE%3D&expires=8h&chkv=0&chkbd=0&chkpc=&dp-logid=244214399352473502&dp-callid=0&size=c1600_u1600&quality=100&vuk=-&ft=video"></image>
</details>
