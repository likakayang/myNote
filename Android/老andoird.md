各个类型APP概述  
1、游戏类。有自己的一套在线更新流程。 lua之类的脚本。   
2、手机助手、手机卫士。对Service、Receiver、ContentProvider使用较多，四大组件都要插件化。  
3、音乐、视频、直播。除了Activity对Service和Receiver依赖较强。  
4、电商类、社交类、新闻类、阅读类。基本都是Activity。



handler是android中更新UI、处理消息的一个机制。  
	Android在设计时，封装了一套消息创建、传递、处理机制。如果不遵循这种机制没办法更新UI信息，会抛出异常。  

handler获取当前现成的looper对象，looper从MessageQueue中取出Message，然后handler对这些message进行分发和处理。

两个拖拽API  
1、ViewDragHelper    
2、onDragListener  
    最上层，图块，跨进程拖拽   
Androidx中NestedScrollView，同向滑动，子View优先。



数据存储  
安全  
SQLite->SharePreference->ContentProvider->File I/O->网络存储  
效率  
SQLite->SharePreference=FIle I/O->ContentProvider->网络存储  
量级  
网络存储->File I/O->ContentProvider=SQLite->SharePreference  

权限  
android基于linux内核，而linux权限访问由进程和文件两部分组成。  
1、android所有者权限，相当于Android ROM开发权限。  
2、android root权限，相当于linux系统中最高用户权限。  
3、android应用程序权限，在AndroidManifest中声明，由用户授权使用。



application  
应用程序框架层  
函数库（C和运行库）  
linux内核  


运行库中包含Dalvik库  
Dalvik是android系统运行的虚拟机  
JVM直接运行.class文件，而Dalvik运行.dex文件  
Dalvik是android5.0之前的运行库，5.0之后使用的是ARE  
Dalvik是运行时编译，ARE是安装时编译  

Intent  
显示Intent，明确指定需要启动或性需要触发的组件的类名  
隐式Intent，指定需要启动或触发的组件应满足的条件  


Activity是Window的容器，包含一个getWindow()方法，该方法返回Activity所包含的窗口  
Service用于后台，一般不需要与用户交互  
Broadcast广播  
ContentProvider跨应用数据交换



startActivity()  
startActivityForResult()  
Activity栈，有四种启动模式  


startService()  
bindService()





ANR
1、点击按键或者触摸屏幕等输入时间在5s内没有响应。
2、BoradcastReceiver事件（onReceive()方法中）在规定的时间内没有处理完（前台广播为10s，后台广播为60s）。
3、Service在规定的时间内没有完成启动（前台service为20s，后台service为200s）。
4、ContentProvider的publish在10s内没有完成。




添加第三方库：  
下面分两种情况介绍一下如何导入第三方类库。

　　1、对于jar的类库，非常简单，只要在项目根目录下新建一个libs目录，然后把jar复制进去，在jar上点击右键，选择Add as library，即可完成依赖的添加。

　　2、对于github等网站上下载的源码类库，是无法通过这种方式添加的。首先把git clone下来的整个文件夹放入项目根目录下，这里以我自己的开发包为例，我的开发包名字是ShunixDevKit，里面有一个lib目录才是真正的类库，那么我们要做的就是手动在settings.gradle里面添加：

　　include ':ShunixDevKit:lib'
　　注意，gradle使用:作为路径分隔符。这样Android Studio就知道了我们的类库放在哪里，当然这样还是不够的，要让项目能使用类库，我们还需要添加这个类库作为项目的依赖，选择File->Project Structure，然后选中主module的名称，点击dependencies，添加:ShunixDevKit:lib就可以了，gradle的build就能成功。

以上就是添加第三方类库作为依赖的过程。这里需要注意一下的地方就是，导入的类库根目录下的gradlew文件一定要可执行，否则Android Studio会提示错误，而且根据错误信息很难找出来这个错误，我自己因为这个搞了很久，希望对大家有帮助


Intent七大属性：  
启动： ComponentName、Action、Category  
传值：Data、Type、Extra  
启动模式：Flag  


drawable中的图片命名
			activity名称_逻辑名称/common_逻辑名称
		styles.xml将layout中不断重现的style提炼出通用的style通用组件，放到styles.xml
		使用layer-list和selector和shape
		图片尽量分拆多个可重用的图片
		服务端可以实现就不要放在客户端
		Acticity中尽可能少创建Handler对象，一个主线程Handler，一个后台HandlerThread就可以了
		线程尽可能少用new Thread，多使用AsyncThread
		尽可能减少Layout的嵌套层级。Layout的过度嵌套会造成渲染时开销过大的问题。layout组件化，尽量使用merge及include复用。
		使用尺寸资源的时候尽量使用像素无关单位。字符串尽可能的抽离，使用res/value下的xml文件进行维护。 
        Log（系统名称 模块名称 接口名称 ，详细描述）   




#### 在子线程需要更新UI
1、Handler
2、runOnUiThread
	new Thread(){
		public void run(){
			//执行耗时操作
			runOnUiThread(new Runnable(){
				@Override
				public void run(){
					//更新UI
				}
			});
		
		}
	}
3、View.post(Runnable r)

　　



#### 实例化LayoutInflater
1、LayoutInflater inflater=getLayoutInflater();
2、LayoutInflater inflater=LayoutInflater.from(this);
3、LayoutInflater inflater=(LayoutInflater)Context.getSystemService(LAYOUT_INFLATER_SERVICE);



#### 疯狂android讲义
Activity和Sevice都继承了Context，所以Activity和Service都可以直接作为Context使用。  

