# Linux-Shell-netstat--s-And-download-photo
 linux shell实现观察tcp活动状态以及下载图片  
 
## 上面的文件中：
### 1.tcp.sh 观察tcp活动状态
#### 简单描述
1. `netstat --statistics`命令可以列出tcp等协议的统计信息。  
2. 编写shell脚本程序，每隔1分钟生成1行信息：当前时间；这一分钟内TCP发送了多少报文；接收了多少报文；收发报文总数；行尾给出符号+或-或空格（`+`表示这分钟收发报文数比上分钟多10包以上，差别在10包或以内用空格，否则用符号`-`）

#### 输入格式：./tcp.sh

### 2.bing.sh 下载https://bing.ioliu.cn/?p= 网站上图片
#### 简单描述
1. 访问[必应图像网站](https://bing.ioliu.cn/?p=23)可以看到bing图库第23页的内容（见下一PPT中的图片），这个Web页有多个图片小样，将鼠标放到某个小样上，如右上角，可见中文说明信息`“野花草甸上的一只欧亚雕鸮，德国莱茵兰-普法 尔茨”`和`日期信息2019-08-03`，点击一下，此图片就可以下载。  
2. 编写脚本 程序 bing.sh，将这个图库中照片全部下载下来存放到本地`bing目录`中，上面URL中`p=23`可以换成`p=1`到`p=126`可访问126个页，每页有12个图， 每个图的日期，中文说明信息和下载地址及文件名 html文件中可提取。要求下载后的文件命名为`“日期 中文说明.jpg”`例如：`2019-08-03 野花草甸上 的一只欧亚雕鸮，德国莱茵兰-普法尔茨.jpg`  
3. 对已设计好的`bing.sh`进一步扩充，允许下面的命令行参数：`./bing.sh rand 500`，实现的功能为：执行500次随机获取。每次成功的随机获取会得到一个图片，检查一下这个图片是否本地已存在。如果已存在，丢弃，否则保 存。 访问 https://bing.ioliu.cn/v1/rand?type=json 可得到一个 json 数据，每 次 得到的内容是随机的，其中含有图片的日期、说明信息和获取它的 url 网 址。新获得的 文件命名方式与以前的程序相同。  
**要求**：文件名不同但是内容完全相同的图片丢弃，例如，下面两个文件虽然名字不同，但是内容是一样的，只保留其中一个文件。 `2019-05-03 Ruff male displaying its plumage, Varanger Peninsula, Norway.jpg`和`2019-05-02 挪威瓦朗厄尔半岛上一只展示 翎颌的雄性涉禽.jpg ` 

#### 相关文件：
+ bing_rand.sh 可以实现随机下载的  
- bing_rand_concur.sh 除了随机下载，还是实现了并发    
+ bing_up.sh 代码比较简洁（没有并发）  

#### 输入格式：   
+ ./bing.sh 1 3 # 下载1~3页的图片（1页有12张）  
- ./bing.sh rand 50 # 随机下载50次  
