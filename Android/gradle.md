相应版本的gradle plugin不支持过低版本的gradle以及SDK

在项目的build.gradle文件中buildscript里dependencies的classpath设置的是gradleplugin的版本，其中文件第一行是：apply plugin:'com.android.application'，其作用是声明了当前模块的gradle引用项目的gradle配置



application下的build.gradle

在项目的build.gradle文件中，如下所示：

```groovy
// Top-level build file where you can add configuration options common to all sub-projects/modules.
buildscript {
    repositories {    
        jcenter()
    }
    dependencies {
        classpath 'com.android.tools.build:gradle:2.3.3'

        // NOTE: Do not place your application dependencies here; they belong
        // in the individual module build.gradle files
    }
}
allprojects {
    repositories {
        jcenter()
    }
}
task clean(type: Delete) {
    delete rootProject.buildDir
}
```

buildscript标签是gradle plugin的下载配置信息，depenndencies配置的是gradle pugin的版本，语法格式是group:name:version

allprojexts标签是最高级项目及子项目的配置性信息，task clean声明了一个Delete类型的clean任务，将删除rootProject.buildDir信息

#### application下的settings.gradle

在项目的settings.gradle文件中，有这么一句include':app',':mvpDemo',声明了app与mvpDemo这两个模块属于gradle构建



#### module下的build.gradle

在模块的build.gradle中，如下所示

```groovy
apply plugin: 'com.android.application'

android {
    compileSdkVersion 26
    buildToolsVersion "26.0.0"

    defaultConfig {
        applicationId "com.example.myapplication"
        minSdkVersion 15
        targetSdkVersion 26
        versionCode 1
        versionName "1.0"

        testInstrumentationRunner "android.support.test.runner.AndroidJUnitRunner"

    }
    buildTypes {
        release {
            minifyEnabled false
            proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
        }
    }
}

dependencies {
    compile fileTree(dir: 'libs', include: ['*.jar'])
    androidTestCompile('com.android.support.test.espresso:espresso-core:2.2.2', {
        exclude group: 'com.android.support', module: 'support-annotations'
    })
    compile 'com.android.support:appcompat-v7:26.+'
    compile 'com.android.support.constraint:constraint-layout:1.0.2'
    testCompile 'junit:junit:4.12'
}
```

第一行声明了该模块的gradle配置引用新项目的gradle配置

compileSdkVersion和buildToolsVersion与Android SDK的关联，并且应该永远是各自最新版本

applicationId是基于创建应用程序时指定的域名和项目名称，避免不同应用冲突

minSdkVersion是意愿为此应用程序支持的最小AndroidAPI，而targetSdkVersion是目标Android版本

versionCode用于识别的版本号

versionName用于自己的内部版本跟踪

testInstrumentationRunner属性配置为使用Android应用程序配置的JUnit4测试运行器

buildTypes支持构建两种类型，分别为release和debug。没有写明debug，debug使用默认设置



fileTree(dir:'libs',include:[''*jar'])是fileTree将文件libs中的任何jar文件添加到编译类路径的依赖项

androidTestCompile依赖性是指Espresso的测试库，用于Android应用程序的集成测试

com.android.support.appcompat-v7:26.+将Android兼容性库添加到项目中。这允许您在任何Android应用程序需中使用与SDK版本7一样的材料设计主题和其他功能

com.android.support.constraint:constraint-layout:1.0.2将新的约束布局添加到项目中。结合兼容性库，您可以创建具有最新布局功能的应用程序

testCopile即是junit测试的依赖关系

---



参考链接：https://guides.gradle.org/building-android-apps/