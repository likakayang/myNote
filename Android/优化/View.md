优化自定义View
1、	减少在onDraw（）进行大量的计算和对象创建，
2、	减少invalidate（）的使用次数
3、	避免让UI系统遍历整个UI树
4、	复杂的布局直接使用自己的viewgroup来写
