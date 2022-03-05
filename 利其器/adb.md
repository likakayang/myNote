#### Android Debug Bridge



1、查看链接中的手机

```shell
adb devices
```

2、进入手机系统

```shell
adb shell
```

3、在系统环境下查看安装的包

```shell
adb shell pm list packages
pm list packages|grep targetpackage
```

4、查看包的详细信息

```shell
adb shell dumpsys package packagename
```

5、包的所有权限

```shell
aapt d permissions /path/to/com.yourpackage.apk
```

6、查看系统日志

```shell
adb logcat
```

7、查看分辨率

```shell
adb shell wm size
```

8、查看是否支持NFC

```shell
adb shell pm list features (如android.hardware.nfc)
```

9、查看内核

```shell
adb shell getprop ro.product.api
```

10、查看SDk版本

```shell
adb shell getprop ro.build.version.sdk
```

11、查看手机型号

```shell
adb shell getprop ro.product.model
```

12、查看手机厂商

```shell
adb shell getprop ro.product.manufacturer
```

13、在设备上安装demo.apk

```shell
adb install demo.apk
```

14、PC文件导入到设备/sdcard/下

```shell
adb push D:/test.txt/sdcard/
```

15、将/sdcard/下文件导出到电脑D盘

```shell
adb pull /sdcard/test.txt D:/
```

16、通过uuid查看链接的特定手机

```shell
adb -s uuid<command>
```

