- #+BEGIN_PINNED
  Peterson, L. L., & Davie, B. S. (2022). Computer networks: a systems approach (6th ed.). Morgan Kaufmann. c1.1
  #+END_PINNED
- 网络在不同人群的视角下是不同的。为了理解和参与网络的设计，需要理解他们的在不同场景下的需求。
	- *和网络交互的人群:*
		- 网络使用者
		- 应用开发者
		- 网络管理者
		- 网络设备制造和协议设计者
- ## 应用的类型
	- *Web*
		- 在一个最基础的用户界面下，用户点击一个地址，然后与这个地址相关的信息会全部呈现到浏览器。这个地址叫作URL(统一资源定位符)
			- ```text
			  http://www.cs.princeton.edu/~llp/index.html
			  ```
			- `http`指示了获取信息的协议
			- `www.cs.princeton.edu`指示了提供服务的机器的名字
			- `~llp/index.html`唯一指定了要访问的内容
		- 点击一个地址可能会产生超过12条信息被交换，如果网页有嵌入的对象的话交换的还会更多。
			- 这些信息中有接近6条用于将服务器名字(`www.cs.princeton.edu`)翻译成IP地址(`128.112.136.35`)
			- 3条信息用于设置浏览器和目标服务器之间的TCP(`Transmission Control Protocol`)连接
			- 4条信息用于浏览器发送HTTP `get`请求和服务器返回页面
			- 4条信息用于断开TCP连接
	- *The delivery of "streaming " audio and video*
		- 视频网站和互联网电台需要这样的技术，有时候人们看视频或者听广播不希望把整个文件都下载下来，而是按照自己的需求选取其中的一些部分。
			- 它和获取网页信息的不同之处在于，不连贯的信息是不能容忍的。网页信息可以分模块展现，而视频和音频信息却不能被跳过或者打乱。
	- *Real-time audio and video*
		- 它比*"streaming" audio and video*有更紧的时间容忍度，通常用在视频会议或者网络电话，它的视频流和声音流是双向的，而*"streaming" audio and video*是单向的。