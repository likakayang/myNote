View概述  
* implements 
-Drrawable.Callback,
-KeyEvent.Callback,
-AccessibilityEventSource  


## 自定义View
### 绘制(Drawable.Callback)和事件监听(KeyEvent.Callback)
```java
View implements Drawable.Callback,KeyEvent.Callback,AccessibilityEventSource
```

#### Drawable.Callback
invalidateDrawable(Drawable who)  
scheduleDrawable(Drawable who,Runnable what,long when)  
unscheduleDrawable(Drawable who,Runnable what)

#### KeyEvnet.Callback
onKeydown(int keyCode,KeyEvent event)  
onKetLongPerss(int keyCode,KeyEvent event)  
onKeyup(int keyCode,KeyEvent event)  
onKeyMultiple(int keyCode,int count,KeyEvent event)

#### AccessibilityEventSource()
sendAccessibilityEvent(int eventType)  
sendAccessibilityEventUnchecked(AccessibilityEvent event)  

### ViewManager
addView()  
updateViewLayout()  
removeView()

---
### 绘制
重写onDraw()  
Canvas Paint


### 几何变换
Canvas Matrix Camera


### View绘制流程  




#### 自定义View  
三要素：布局、回执、触摸反馈  

绘制：控件内容的显示  
>使用API对控件进行设置，然后控件自己完成绘制过程。  


```
public class MyView extends View{
    ...
    @override
    onDraw(){
        super.onDraw();
        ...//MyView绘制
    }
    ...
}

```


常用的绘制方法onDraw()主体绘制，还有负责绘制前景、背景、整体  
Canvas    Paint  

clip裁切  
几个变换（端点的拉扯变化）  

重写onDraw()方法  
Canvas中两个关键方法drawXXX()关键参数Paint，clipXXX()几个变换