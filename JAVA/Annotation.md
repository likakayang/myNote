@author  
    标明开发该模块的作者  

@version  
    该模块的版本  

@see  
    参考转向，也就是相关主题  

@param  
    对方法中某参数的说明  

@return  
    对方法返回值的说明  

@exception  
    对方法可能抛出的异常进行说明  


在JDK1.5中出现  
Java提供了一种原程序中的元素关联任何信息和任何元数据的途径和方法。  

JDK自带注解：  
@Override  覆盖父类方法  
@Deprecated  过时  
@Suppvisewarnings 忽视警告  

注解分类  
按照运行机制分类  
1、源码注解  只在源码中存在，编译成.class文件不存在了  
2、编译时注解  在源码和.class文件中都存在  
3、运行时注解  在运行阶段还起作用，甚至会影响逻辑的注解  

元注解（注解的注解）  
@Target({ElementType.METHOD,ElementType.TYPE})   作用域 CONSTRUCTOR（构造方法声明）, FIELD（字段声明）, LOCAL_VARIABLE（局部变量声明）, METHOD（方法声明）, PACKAGE（包声明）, PARAMETER（参数声明）, TYPE（类，接口）  
@Retention(RetentionPolicy.RUNTIME)  生命周期  SOURCE, CLASS, RUNTIME  
@Inherited  标识性的元注解 允许子类继承  
@Documented  生成javadoc时会包含注解  

自定义注解  
自定义注解的语法要求  
       使用@interface关键字定义注解  
       成员以无参无异常方式声明  
       可以使用default为成员指定一个默认值  
       成员的类型是受限的，合法的类型包括基本类型及String，Class，  Annotation，Enumeration  
       如果只有一个成员，则成员名必须取名为value()，在使用时可以忽略成员名和赋值号（=）  
       注解可以没有成员，成为标识注解  
   使用自定义注解的语法  
       @<注解名>（<成员名1>=<成员值1>,...）    

       
解析注解  

       通过反射获取类、函数或成员上的运行时注解信息，从而实现动态控制程序运行的逻辑。
    1、使用类加载器加载类
      Class c=Class.forName("");
    2、找到类上面的注解
      boolean isExist=c.isAnnotationPresent(Description.class);
    3、拿到注解实例
      Description d=(Description)c.getAnnotation(Description.class);
    4.找到方法上的注解
      Method[] ms=c.getMethods();
      for(Method m:ms){
          Description d=(Description)m.getAnnotation(Description.class);
          m.getAnnotation();
      }
      另一种方法
      for(Method m:ms){
          Annotations[] as=m.getAnnotations();
          for(Annotation a:as){
              if(a instanceof Description){
                Description d=(Description)a;
               }   
          }
      }
