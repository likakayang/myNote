View概述  
* implements 
-Drrawable.Callback,
-KeyEvent.Callback,
-AccessibilityEventSource  


### 自定义View  
## 绘制(Drawable.Callback)和事件监听(KeyEvent.Callback)
```
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


### 动画