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