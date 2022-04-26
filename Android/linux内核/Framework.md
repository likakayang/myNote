### PMS（PackageManagerService）  
PMS是系统进程，无法Hook。通过Binder机制进行与客户端的通信。  
Binder服务端：即系统服务PackageManagerService extends IPackageManager.Stub  
Binder客户端：即应用层常用的PackageManager，实际上PackageManager是个抽象类，直接使用的是ApplicationPackageManager


android系统每次启动时，都会使用PMS把Android系统中所有的apk安装一遍。  
1、读取安装时保存的APP安装信息。  
2、扫描/安装保存在特定目录下的apk。  
3、分配用户组id。  
4、安装信息写入本地文件。  

#### AndroidManifest文件  
——四大组件信息，如：静态Receiver，默认启动的Activity  
——分配用户ID和用户组ID  
>用户ID唯一，因为Android是一个linux系统。  
>用户组ID指各种权限，每个权限都在一个用户组中，分配了哪些用户组ID，就拥有哪些权限。  

——在Launcher生成一个icon，icon保存着默认启动的Activity的信息。  
——在App安装的最后，把上面的信息记录在一个xml文件中，以备下次安装时再次使用。  


#### 系统中各类apk路径  
-data/app-private 受DRM保护的App  
-data/app 用户自己安装的App  
-data/framework 资源型App，用于打包  
-system/app 系统自带的app  
-render/app 设备厂商提供的App  

PMS中有一个类PackageParser，专门解析AndroidManifest，以获取四大组件以及用户权限。  
PackageParser不对App开发人员开放，可以通过反射来获取类。  
PackageParser中有一个方法parsePackage，接受一个apkFile的参数，，既可以是当前apk文件，也可以是外部apk。返回的是Package类型的实体对象，存储着四大组件的信息。  
>Package类型一般不用，通过generatePackageInfo方法，转为PackageInfo类型。  

插件化编程中，反射PackageParser，来获取插件AndroidManifest中的四大组件信息。  

开发人员可使用Context.getPackageManager()来获取当前Apk信息。
>该方法返回的是ApplicationPackageManager类型的对象。是PackageManager的子类。  

ApplicationPackageManager其实是一个壳，装饰器模式。装饰了ActivityThread.getPackageManager()  

ServiceManager是一个字典容器，存放着各种系统服务。当kdy为clipboard，对应剪切板。key为package，对应PMS。  

插件化编程中，反射ActivityThread获取Apk包中的信息。一般用于宿主Apk。  

Android插件化能从外部下载一个apk插件，在于ClassLoader。  
>重要的是PathClassLoader和DexClassLoader。参数optimizedDirectory，缓存需要加载的dex文件，并创建一个DexFile对象。  
DexClassLoader可以指定optimizedDirectory，加载外部dex复制到内部路径。  
dex，jar，apk也可以sd卡加载。  

ClassLoader双亲委托。  
ClassLoader加载类时，会优先父类去加载。  
zeus插件化框架，替换ClassLoader。
