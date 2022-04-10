java窗口输出乱码  
在.vscode的settings.json中添加如下：  
```
"code-runner.executorMap": {
        
        "java": "cd $dir && javac -encoding utf-8 $fileName && java $fileNameWithoutExt"
    },
    "code-runner.runInTerminal": trues
```